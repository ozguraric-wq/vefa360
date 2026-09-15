# VEFA360 — Emekten geleceğe

VEFA360 proje tanıtımı ve etkileşimli demo web sitesi. GitHub Pages yayın hedefi:
https://ozguraric-wq.github.io/vefa360/

## Demo kapsamı

- Video giriş, yedi aşamalı yolculuk, 16 Akademi modülü ve 12 iş paketi.
- 12 kurgusal hesap; satıcı vitrini, sertifika ID/QR sorgulama.
- Katılımcı, partner ve yönetim panelleri; sınav, uygulama, avantaj kodu ve ticari hazırlık senaryoları.
- Sertifika önce kazanılır; şirket/muafiyet hazırlığı ve ticari aktivasyon sonrasında gelir.
- Tüm hesaplar, markalar, belgeler, avantajlar ve işlemler kurgusaldır. Resmî hizmet veya onay değildir.
- Veriler yalnızca açık sayfanın belleğinde tutulur; yenilemeyle başlangıca döner. Gerçek kimlik belgesi, başvuru, ödeme veya kurum entegrasyonu yoktur.

## GitHub Pages yayını

`docs/`, derlenmiş ve doğrudan yayımlanabilir sürümdür. GitHub üzerinde derleme veya sunucu gerektirmez.

1. Dosyaları `ozguraric-wq/vefa360` deposunun `main` dalına yükleyin.
2. Depoda **Settings → Pages → Build and deployment → Source: Deploy from a branch** seçin.
3. Dal **main**, klasör **/docs**, ardından **Save** seçin.
4. GitHub Pages dağıtımı tamamlandığında yukarıdaki adresi açın.

`docs/.nojekyll` dosyasını koruyun. Hash tabanlı gezinme sayesinde demo ve sertifika bağlantıları sayfa yenilemede de çalışır.

## Geliştirme ve güncelleme

Node.js 22.13 veya üstü ve `package.json` içinde sabitlenen pnpm sürümünü kullanın.

```sh
pnpm install --frozen-lockfile
pnpm dev:pages
pnpm build:pages
```

Son komut `docs/` klasörünü yeniden oluşturur. Kaynak değişiklikleriyle birlikte güncel `docs/` çıktısını da commit edin; Pages bu çıktıyı yayımlar. Kilit dosyasını koruyun.

### Yayın adresi ve QR

Bu sürümün taban yolu `/vefa360/` olarak ayarlanmıştır. Başka depo/alan adı kullanılırsa `vite.pages.config.ts`, `index.html` ve `scripts/generate-pages-qr.py` içindeki yayın adreslerini birlikte güncelleyin. QR görüntüleri repoda hazırdır; normal derleme Python gerektirmez. Sertifika ID veya yayın adresi değiştiğinde Python 3 ve `reportlab` ile önce şu komutu çalıştırın:

```sh
python3 scripts/generate-pages-qr.py
pnpm build:pages
```

`public/qr/destinations.json` kodların hedeflerini listeler. QR, oturumdaki değişiklikleri taşımaz; yeni cihazda başlangıç demo kaydını açar.

## İçerik ve medya

İçerik, VEFA360 proje dosyasının finansal tutarlar çıkarılmış nihai sürümünü temel alır. Program hedefleri gerçekleşmiş sonuçlardan ayrı etiketlenir. Kullanılan görüntüler temsili stok medyadır; kaynak ve lisans bilgileri `media-sources.json` içindedir.

Önceki barındırma sürümü için mevcut dosyalar korunmuştur. GitHub Pages için kullanılacak komut `build:pages`, yayın klasörü `docs/` klasörüdür.
