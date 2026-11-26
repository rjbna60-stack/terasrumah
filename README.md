# Menu Digital Teras Rumah Cafe & Resto

Web pemesanan untuk pelanggan (dibuka lewat HP, bisa dipasang QR di meja).

## File
- `index.html` : halaman pelanggan (menu, keranjang, pesan, pembayaran Tunai/Transfer/QRIS, status pesanan)
- `staff.html` : panel kasir dan admin (login, pesanan masuk, ubah status)
- `aturan_firestore.txt` : aturan keamanan database Firebase
- `.nojekyll` : agar GitHub Pages menampilkan file apa adanya

## Cara pasang di GitHub Pages
1. Buat akun di github.com, lalu klik **New repository**. Beri nama, misalnya `menu-teras-rumah`, pilih **Public**, klik Create.
2. Klik **uploading an existing file**, seret semua file dari folder ini (termasuk `.nojekyll`), lalu **Commit changes**.
3. Buka **Settings → Pages**. Di Source pilih **Deploy from a branch**, branch `main`, folder `/ (root)`, klik Save.
4. Tunggu 1-2 menit. Alamat web muncul di halaman itu:
   `https://NAMA-GITHUB.github.io/menu-teras-rumah/`
5. Buat ulang QR dari alamat tersebut.

## Mengaktifkan pesanan masuk ke kasir (opsional)
Tanpa langkah ini, web tetap bisa dipakai pelanggan, tapi pesanan tidak sampai ke panel kasir.
1. Buat project di Firebase (console.firebase.google.com): aktifkan Firestore dan Authentication (Email/Password), lalu tambahkan akun admin dan kasir.
2. Tempel isi `aturan_firestore.txt` ke Firestore Rules (ganti email contoh).
3. Salin `firebaseConfig`, lalu isi pada baris `const FB=...` di `index.html` dan `staff.html`. Di `staff.html` ganti juga `ADMIN=["admin@contoh.com"]` dengan email admin.
4. Commit ulang kedua file. Panel kasir ada di `.../staff.html`.

## Yang perlu diganti
- Rekening transfer di `index.html`: cari `BANK={n:"BSI",r:"0000000000",a:"Teras Rumah"}`.
- Nomor WhatsApp kasir di `index.html`: cari `const WA0=""` dan isi misalnya `"0812xxxxxxx"`.
