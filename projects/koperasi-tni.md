# 🏦 Sistem Informasi Manajemen Koperasi & ERP Terintegrasi (Koperasi TNI)

> **Status:** Production (Digunakan oleh Koperasi Balai Sudirman/TNI)
> **Role:** Fullstack Developer
> **Type:** ERP / B2B Enterprise System

### 📖 Executive Summary

Proyek ini adalah solusi **All-in-One ERP** yang dirancang untuk memodernisasi ekosistem Koperasi TNI. Sistem ini menggabungkan manajemen keanggotaan (Simpan Pinjam) dengan operasional bisnis riil (Ritel/Jasa) dalam satu database terpusat.

**Masalah Utama yang Diselesaikan:**
Sebelumnya, pencatatan transaksi kasir, simpan pinjam, dan penggajian dilakukan terpisah, menyebabkan ketidakcocokan data akuntansi (human error) dan laporan keuangan yang terlambat.

**Solusi:**
Membangun sistem dengan **"Financial Logic Engine"** di mana setiap transaksi operasional (Front-end) secara otomatis menjurnal dirinya sendiri ke dalam buku besar akuntansi (Back-end) secara real-time.

---

### ⚙️ Key Technical Features

#### 1. Core Banking System (Simpan Pinjam)

Modul untuk mendigitalkan siklus hidup anggota koperasi.

* **Member Lifecycle:** Pendaftaran digital, status keaktifan, dan profil.
* **Financial Products:** Manajemen Simpanan (Pokok/Wajib/Sukarela) dan Pinjaman (Approval workflow, perhitungan bunga/bagi hasil otomatis).
* **Settlement:** Manajemen AR/AP anggota dan rekonsiliasi Bank.

#### 2. Unit Usaha & Point of Sales (Retail ERP)

Modul untuk mengelola bisnis ritel milik koperasi (Minimarket/Toko).

* **Omnichannel POS:** Kasir terhubung langsung dengan stok gudang.
* **Inventory Management:** Stok opname, alert stok menipis, dan metode perpetual inventory.
* **Asset Management:** Pencatatan aset tetap dengan **kalkulasi penyusutan otomatis (Depreciation Scheduler)** setiap akhir bulan.

#### 3. HRM & Payroll Automation

Sistem penggajian yang terintegrasi dengan mesin absensi fisik.

* **Smart Sync Fingerprint:** Sinkronisasi *real-time* data kehadiran dari mesin fisik ke cloud server.
* **Complex Payroll Logic:** Kalkulasi otomatis Gaji Pokok + Tunjangan + Lembur (berdasarkan log jam) - Potongan (BPJS/PPh 21/Kasbon).
* **Tax Engine:** Perhitungan estimasi PPh 21 karyawan otomatis.

---

### 🧠 The "Secret Sauce": Automated Financial Logic

Fitur paling kompleks dalam sistem ini adalah **Auto-Journaling Engine**. Sistem menerjemahkan transaksi bisnis menjadi jurnal akuntansi standar PSAK tanpa intervensi manual.

| Tipe Transaksi | Trigger (Aktivitas User) | Logika Backend (Auto-Journal) |
| :--- | :--- | :--- |
| **Simpanan** | Teller input setoran anggota | `(Dr) Kas/Bank` <br> `(Cr) Liabilitas Simpanan` |
| **Penjualan Ritel** | Kasir cetak struk | 1. `(Dr) Kas` & `(Cr) Pendapatan` <br> 2. `(Dr) HPP` & `(Cr) Persediaan` (Update Stok) |
| **Pembelian Aset** | Procurement beli aset | `(Dr) Aset Tetap` <br> `(Cr) Kas/Hutang` |
| **Payroll Run** | HR Approve Gaji | `(Dr) Beban Gaji` <br> `(Cr) Hutang Gaji / Bank` |
| **Penyusutan** | Scheduler (Akhir Bulan) | `(Dr) Beban Penyusutan` <br> `(Cr) Akumulasi Penyusutan` |

---

### 📸 Gallery & Implementation

<!-- Ganti LINK_GAMBAR di bawah dengan url gambar yang sudah diupload ke repo -->
| Dashboard Monitoring Stok | Laporan Keuangan (PHU) |
| :---: | :---: |
| ![Dashboard Stok](LINK_GAMBAR_DASHBOARD_STOK) | ![Laporan PHU](LINK_GAMBAR_LAPORAN_PHU) |
| *Real-time stock movement monitoring* | *Auto-generated Balance Sheet & Profit/Loss* |

| Point of Sales | General Ledger |
| :---: | :---: |
| ![POS System](LINK_GAMBAR_POS) | ![Buku Besar](LINK_GAMBAR_BUKU_BESAR) |
| *Kasir ritel terintegrasi* | *Drill-down detail per akun akuntansi* |

---

### 🚀 Business Impact

* **70% Efisiensi Waktu:** Memangkas waktu rekapitulasi manual administrasi.
* **Zero Human Error:** Mencegah kesalahan debit/kredit manual dalam pembukuan.
* **Transparansi:** Laporan Keuangan (Neraca/Laba Rugi) tersedia kapan saja (real-time) untuk keperluan Rapat Anggota Tahunan (RAT).

### 🛠 Tech Stack

* **Backend:** [Laravel / Node.js], MySQL (Complex Queries & Stored Procedures).
* **Frontend:** [Vue.js / React], Bootstrap/Tailwind.
* **Integration:** Fingerprint SDK, REST API.
