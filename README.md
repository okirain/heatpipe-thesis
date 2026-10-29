# Skripsi Quarto dan Simulator Pipa Kalor Natrium

**Penulis:** Muhammad Naufal Tamimi  
**NIM:** 20/456315/TK/50445

## Isi proyek

- `Skripsi.qmd`: dokumen utama dengan halaman awal dan seluruh bab.
- `chapters/`: Bab I–VI dan daftar pustaka.
- `appendices/`: listing program dan pengujian.
- `src/heatpipe_simulator.py`: simulator aliran dua fase tereduksi orde satu dimensi.
- `tests/test_simulator.py`: sepuluh pengujian otomatis.
- `data/`: keluaran numerik CSV/JSON.
- `figures/`: gambar yang dihasilkan ulang oleh program.
- `_quarto.yml` dan `ugm-style.tex`: konfigurasi Quarto dan gaya PDF mengikuti templat UGM yang diberikan.

## Menjalankan simulasi

Dari direktori proyek:

```bash
python -m pip install -r requirements.txt
python src/heatpipe_simulator.py
python -m unittest discover -s tests -v
```

Program menulis ulang berkas pada `data/` dan `figures/`. Parameter acuan berada pada dataclass `HeatPipeGeometry` dan `OperatingConditions` di dalam sumber. Semua satuan internal adalah SI.

## Merender skripsi

Dengan Quarto dan Tectonic terpasang:

```bash
quarto render Skripsi.qmd --to pdf
```

Hasil ditulis ke `_book/Skripsi.pdf`. Nama pembimbing, tanggal, tahun terdaftar, dan rincian pengesahan sengaja dibiarkan sebagai placeholder untuk dilengkapi.

## Batas penggunaan

Model adalah model tunak satu dimensi dengan kesetimbangan jenuh, aliran uap tereduksi, dan aliran balik cairan Darcy. Model bukan CFD, tidak menyelesaikan antarmuka dua fase, dan tidak mencakup start-up beku, gas takterkondensasi, radiasi terperinci, atau kegagalan material. Batas sonik, entrainment, dan pendidihan adalah persamaan penyaringan rekayasa. Hasil belum divalidasi dengan eksperimen dan tidak boleh digunakan sebagai satu-satunya dasar desain atau keselamatan reaktor.
