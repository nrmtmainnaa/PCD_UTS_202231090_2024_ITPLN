# PCD_UTS_202231090_2024_ITPLN

#Nomor 1

analisa pada codingan deteksi warna pada citra yaitu yang pertama ada `red = image[:, :, 0]` gunanya untuk Memisahkan saluran warna merah dari citra. `image[:, :, 0]` ini mengambil semua baris dan kolom, tetapi hanya saluran pertama dari citra (indeks 0 adalah saluran merah dalam citra RGB). `green = image[:, :, 1]` untuk Memisahkan saluran warna hijau dari citra. `image[:, :, 1]` mengambil semua baris dan kolom, tetapi hanya saluran kedua dari citra (indeks 1 adalah saluran hijau dalam citra RGB). `blue = image[:, :, 2]` untuk Memisahkan saluran warna biru dari citra. `image[:, :, 2]` mengambil semua baris dan kolom, tetapi hanya saluran ketiga dari citra (indeks 2 adalah saluran biru dalam citra RGB). `f, (y1, y2, y3, y4) = plt.subplots(1, 4, figsize=(20,10))`: Membuat subplot dengan satu baris dan empat kolom, dengan ukuran total gambar 20x10 inci. Variabel `f` adalah objek figur dan `(y1, y2, y3, y4)` adalah objek sumbu (axes). `y1.set_title('Citra Kontras')`: Memberikan judul "Citra Kontras" pada sumbu pertama (`y1`). `y1.imshow(image)`: Menampilkan citra asli pada sumbu pertama. `y1.axis('off')`: Menghilangkan sumbu pada sumbu pertama, sehingga tidak menampilkan label sumbu. `y2.set_title('Biru')`: Memberikan judul "Biru" pada sumbu kedua (`y2`).`y2.imshow(blue, cmap='gray')`: Menampilkan saluran warna biru dalam skala abu-abu pada sumbu kedua. `y2.axis('off')`: Menghilangkan sumbu pada sumbu kedua.`y3.set_title('Merah')`: Memberikan judul "Merah" pada sumbu ketiga (`y3`). `y3.imshow(red, cmap='gray')`: Menampilkan saluran warna merah dalam skala abu-abu pada sumbu ketiga.`y3.axis('off')`: Menghilangkan sumbu pada sumbu ketiga. `y4.set_title('Hijau')`: Memberikan judul "Hijau" pada sumbu keempat (`y4`). `y4.imshow(green, cmap='gray')`: Menampilkan saluran warna hijau dalam skala abu-abu pada sumbu keempat.`y4.axis('off')`: Menghilangkan sumbu pada sumbu keempat.
selanjutnya membuat codingan histogram gunanya untuk efektif menghitung dan memvisualisasikan histogram untuk channel biru, hijau, dan merah dari sebuah gambar.

#Nomor 2
1. Pendefinisian Range Warna:

Kode ini mendefinisikan beberapa set batas bawah dan atas untuk komponen Hue (H), Saturation (S), dan Value (V) dari ruang warna HSV.
low_blue, up_blue: Mendefinisikan range untuk warna biru.
low_green, up_green: Mendefinisikan range untuk warna hijau.
low_red1, up_red1 dan low_red2, up_red2: Mendefinisikan dua range untuk warna merah, kemungkinan untuk menangani putaran di sekitar lingkaran Hue dalam model HSV.
2. Pembuatan Masker Menggunakan Thresholding:

cv2.inRange: Fungsi ini digunakan untuk membuat masker biner untuk setiap range warna. Ini mengidentifikasi piksel dalam hsv_image yang berada dalam batas bawah dan atas yang ditentukan untuk setiap komponen warna (H, S, V).
mask_blue: Masker untuk piksel di dalam range biru.
mask_green: Masker untuk piksel di dalam range hijau.
mask_red1: Masker untuk piksel di dalam range merah pertama.
mask_red2: Masker untuk piksel di dalam range merah kedua.
mask_red: Menggabungkan mask_red1 dan mask_red2 menggunakan operasi OR bitwise (cv2.bitwise_or) untuk membuat masker merah terpadu.
3. Penggabungan Masker dan Pembuatan Output Akhir:

cv2.bitwise_or: Fungsi ini digunakan untuk menggabungkan masker.
mask_red_blue: Menggabungkan mask_red dan mask_blue untuk mengidentifikasi piksel yang termasuk dalam range warna merah atau biru.
mask_red_blue_green: Menggabungkan mask_red_blue dan mask_green untuk mengidentifikasi piksel yang termasuk dalam warna merah, biru, atau hijau.
4. Konversi Grayscale dan Visualisasi:

Kode tersebut mengkonversi gambar berwarna asli (color_image) menjadi grayscale menggunakan cv2.cvtColor untuk keperluan visualisasi.
Terakhir, ia menggunakan plt.imshow untuk menampilkan berbagai output:
Gambar biner setelah thresholding (binary1)
Masker warna individual (mask_blue), masker gabungan (mask_red_blue, mask_red_blue_green).
