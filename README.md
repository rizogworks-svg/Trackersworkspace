# Trackers Workspace

Versi production yang dirapikan khusus untuk GitHub Pages dan instalasi PWA Android.

## Struktur

```text
Trackers-Workspace/
├── index.html
├── manifest.webmanifest
├── sw.js
├── .nojekyll
├── assets/
│   ├── css/
│   │   └── app.css
│   ├── js/
│   │   ├── storage-guard.js
│   │   ├── config.js
│   │   ├── cloud.js
│   │   ├── pkbon.js
│   │   ├── app.js
│   │   └── boot.js
│   └── img/
│       ├── trackers-logo.png
│       ├── icon-192.png
│       ├── icon-512.png
│       └── icon-maskable-512.png
└── supabase/
    └── 001_user_state.sql
```

## Upload ke GitHub baru

1. Buat repository baru, misalnya `trackers-workspace`.
2. Extract ZIP ini.
3. Upload **isi folder `Trackers-Workspace`** ke root repository. `index.html` harus terlihat langsung di halaman utama repo, bukan berada di folder `frontend`.
4. Buka **Settings → Pages**.
5. Pada **Build and deployment**, pilih **Deploy from a branch**.
6. Pilih branch `main` dan folder `/ (root)`, lalu Save.
7. Setelah deployment selesai, buka URL GitHub Pages yang diberikan GitHub.

## PWA Android

Buka URL GitHub Pages di Chrome Android. Trackers Workspace dapat diinstal dari menu aplikasi atau dari Settings → Install App di dalam webapp.

Jika sebelumnya pernah memasang build lama dari URL yang sama, uninstall PWA lama satu kali atau buka URL di Chrome lalu refresh agar service worker build baru aktif.

## Supabase

Konfigurasi frontend ada di `assets/js/config.js`. File tersebut hanya boleh menggunakan **publishable/anon key**, bukan `service_role` key.

Schema baseline ada di `supabase/001_user_state.sql`. Nama tabel lama `trackly_user_state` sengaja dipertahankan untuk kompatibilitas dengan data/cloud code yang sudah berjalan.

> Jangan mengganti nama tabel atau key internal tanpa migrasi, karena dapat memutus sinkronisasi data lama.
