# Brained - Platform Bimbel Management System

Sistem manajemen bimbingan belajar berbasis terminal yang dibuat dengan Go. Simple tapi powerful buat manage siswa, nilai try out, dan ranking.

![Go Version](https://img.shields.io/badge/Go-1.16+-00ADD8?style=flat&logo=go)

## Tentang Project

Brained adalah aplikasi CLI (Command Line Interface) untuk mengelola data siswa bimbel. Fitur utamanya:

- **Dual User System** - Login sebagai Admin atau Siswa dengan hak akses berbeda
- **Student Management** - Input, edit, hapus data siswa lengkap
- **Try Out Scoring** - Pencatatan dan perhitungan nilai try out otomatis
- **Auto Ranking** - Sistem ranking berdasarkan total nilai
- **Schedule Management** - Pengaturan jadwal les per mata pelajaran

Project ini dibuat untuk tugas akhir mata kuliah Algoritma & Pemrograman menggunakan konsep sorting, searching, array, dan struct.

## Tech Stack

- **Go (Golang)** - Programming language
- Pure stdlib - Gak pake dependency external
- Terminal-based UI dengan formatting sederhana

## Struktur Data

Program ini menggunakan beberapa struktur data utama:

- Array global untuk menyimpan data siswa (max 100)
- Array global untuk menyimpan data admin (max 100)
- Struct untuk user, siswa, mata pelajaran, dan jadwal
- Binary search untuk pencarian by ID (cepat!)
- Linear search untuk pencarian by username
- Selection sort untuk sorting by ID
- Insertion sort untuk ranking by nilai

## Getting Started

### Prerequisites

Yang kamu butuhkan:
- Go 1.16 atau lebih baru ([Download Go](https://golang.org/dl/))
- Terminal/Command Prompt
- Text editor kalau mau edit code

### Running the Program

**Option 1: Langsung jalankan (kalau udah ada .exe)**

Windows:
```bash
# Double click file .exe
# atau via terminal:
brained.exe
```

Linux/Mac:
```bash
chmod +x brained
./brained
```

**Option 2: Compile sendiri dari source**
```bash
# Clone repo
git clone https://github.com/yourusername/brained.git
cd brained

# Run langsung tanpa compile
go run main.go

# Atau compile dulu
go build -o brained main.go

# Jalankan hasil compile
./brained        # Linux/Mac
brained.exe      # Windows
```

**Option 3: Install sebagai global command**
```bash
go install
brained
```

## Cara Pakai

### First Time Setup

1. Jalankan program
2. Pilih menu **Register** (2)
3. Daftar sebagai **Admin** dulu untuk bisa input data siswa
4. Login dengan akun admin yang baru dibuat

### Flow Admin
```
Login → Menu Admin → Input Data Siswa → Input Nilai Try Out → Lihat Ranking
```

Admin bisa:
- Input data lengkap siswa (ID, kelas, mata pelajaran, jadwal)
- Input nilai try out (3x tryout per mata pelajaran)
- Edit atau hapus data siswa
- Lihat ranking semua siswa

### Flow Siswa
```
Register → Login → Lihat Data Diri / Nilai / Ranking / Jadwal
```

Siswa bisa:
- Lihat data pribadi
- Lihat nilai try out sendiri
- Lihat ranking (dibanding siswa lain)
- Lihat jadwal les

## Fitur Unggulan

**🔐 Validasi Input**
- Email harus format valid (@, .)
- Password minimal 6 karakter
- Tanggal lahir format dd/mm/yyyy
- Nilai try out range 0-100
- Username unique (gak boleh sama)

**🔍 Smart Search**
- Binary search untuk cari by ID (super cepat!)
- Linear search untuk cari by username
- Auto-sort sebelum search biar akurat

**📊 Auto Ranking**
- Hitung rata-rata otomatis per mata pelajaran
- Hitung total nilai dari semua mapel
- Ranking update otomatis pakai insertion sort

**⚠️ Error Handling**
- Max 3 percobaan login salah
- Validasi input di setiap form
- Konfirmasi sebelum hapus data

## Project Structure
```
brained/
├── main.go              # Main program file
├── brained.exe          # Compiled executable (Windows)
├── brained              # Compiled executable (Linux/Mac)
└── README.md           # Documentation
```

Single file structure - semua ada di `main.go`:
- Line 1-60: Struct definitions
- Line 61-150: Utility functions (validation, search, sort)
- Line 151-400: Core procedures (register, login, input data)
- Line 401-600: Menu functions (admin & siswa)
- Line 601+: Main function

## Contoh Penggunaan

**Register Admin:**
```
Status: Admin
Nama: John Doe STOP
Username: admin123
Email: admin@brained.com
Password: admin123
```

**Input Data Siswa:**
```
ID: 1001
Kelas: 12 IPA
Telepon: 081234567890
Tanggal Lahir: 15/08/2006
Mata Pelajaran 1: Matematika
Mata Pelajaran 2: Fisika
Mata Pelajaran 3: Kimia
```

**Input Nilai Try Out:**
```
ID Siswa: 1001
[Matematika]
Try Out 1: 85
Try Out 2: 90
Try Out 3: 88
[Fisika]
Try Out 1: 78
...
```

## Limitasi & Constraints

- Max 100 siswa (konstanta NMAX)
- Max 100 admin
- 3 mata pelajaran per siswa
- 3 nilai try out per mata pelajaran
- Data tidak persisten (hilang saat program ditutup)
- Terminal-based, no GUI

## Build untuk Production

**Windows:**
```bash
# Build untuk Windows 64-bit
go build -o brained.exe main.go

# Build dengan size optimization
go build -ldflags="-s -w" -o brained.exe main.go
```

**Linux:**
```bash
GOOS=linux GOARCH=amd64 go build -o brained main.go
```

**Mac:**
```bash
GOOS=darwin GOARCH=amd64 go build -o brained main.go
```

**Cross-compile untuk semua platform:**
```bash
# Windows
GOOS=windows GOARCH=amd64 go build -o brained-windows.exe main.go

# Linux
GOOS=linux GOARCH=amd64 go build -o brained-linux main.go

# Mac
GOOS=darwin GOARCH=amd64 go build -o brained-mac main.go
```

## Algoritma yang Dipakai

- **Binary Search** - O(log n) untuk cari siswa by ID
- **Linear Search** - O(n) untuk cari by username  
- **Selection Sort** - O(n²) untuk sort by ID
- **Insertion Sort** - O(n²) untuk ranking by nilai
- **Sequential Processing** - Input dan validasi data

## Credits

Dibuat sebagai tugas akhir Algoritma & Pemrograman.

---

Made with ❤️by [sayyeone](https://github.com/sayyeone)

