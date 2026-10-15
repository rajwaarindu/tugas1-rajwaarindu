# Data Tugas 1

## Dataset yang Dipilih

| Item | Isi |
|---|---|
| Nama dataset | mC4 Indonesia (`indonesian-nlp/mc4-id`) |
| Subset | `large/partial-train`, dua file Parquet |
| Sumber | https://huggingface.co/datasets/indonesian-nlp/mc4-id |
| Lisensi/ketentuan pakai | ODC-BY; ketentuan penggunaan Common Crawl juga berlaku |
| Ukuran | 580.113.521 byte (sekitar 580,11 MB) |
| Jumlah baris | 305.000 |
| Jumlah kolom | 3 |
| Periode timestamp | 2013-05-18 05:01:28 UTC sampai 2020-08-15 21:24:00 UTC |
| Unit analisis | Satu dokumen teks hasil ekstraksi halaman web |

## Struktur Data

Dataset memiliki tiga kolom:

- `text`: isi teks hasil ekstraksi halaman web.
- `timestamp`: waktu ekstraksi yang dicatat pada dataset.
- `url`: alamat halaman web sumber.

## Berkas Data Mentah

| Nama file | Ukuran (byte) |
|---|---:|
| `mc4_id_0000.parquet` | 289.049.658 |
| `mc4_id_0001.parquet` | 291.063.863 |

Lokasi file di dalam project:

- `data/raw/mc4_id_0000.parquet`
- `data/raw/mc4_id_0001.parquet`

## Pemeriksaan Awal

Hasil profiling awal menggunakan Polars:

- Jumlah baris: 305.000.
- Jumlah kolom: 3.
- Jumlah nilai null: 0 pada ketiga kolom.
- Jumlah teks unik: 305.000.
- Jumlah URL unik: 305.000.
- Rata-rata panjang teks: 3.160,02 karakter.
- Panjang teks minimum: 62 karakter.
- Panjang teks maksimum: 185.713 karakter.
- Jumlah teks kosong atau hanya berisi spasi: 0.

Hasil tersebut diperoleh dari dua file Parquet yang digunakan dalam penelitian tugas ini. Pemeriksaan lanjutan diperlukan untuk mengidentifikasi duplikasi berdasarkan isi teks, nilai yang tidak valid, dan masalah kualitas data lainnya.

## Cara Memperoleh Data

1. Buka halaman dataset mC4 Indonesia di Hugging Face.
2. Unduh file `0000.parquet` dan `0001.parquet` dari subset `large/partial-train`.
3. Simpan kedua file ke folder `data/raw/`.
4. Gunakan notebook `notebooks/01_data_profiling.ipynb` untuk membaca dan memeriksa data menggunakan Polars.

Sumber dataset: https://huggingface.co/datasets/indonesian-nlp/mc4-id

## Aturan Penyimpanan

- Folder `data/raw/` menyimpan file mentah yang tidak diubah.
- Jangan mengunggah atau melakukan commit file Parquet berukuran besar ke GitHub.
- Dokumentasikan sumber dan cara mengunduh dataset agar analisis dapat direproduksi.
- Simpan hasil transformasi pada `data/processed/` jika diperlukan.