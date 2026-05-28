# 📱 Setup VSCode + Deploy ke Vercel (Complete Guide)

## A. Install & Setup VSCode

### Step 1: Download VSCode
1. Buka https://code.visualstudio.com
2. Download sesuai OS kamu (Windows/Mac/Linux)
3. Install seperti biasa (next → next → install)

### Step 2: Install Git (Requirement)
Git digunakan untuk sync file ke GitHub, yang kemudian trigger deploy di Vercel.

**Windows:**
1. Download dari https://git-scm.com/download/win
2. Install (default settings aja, terus next)
3. Verify: Buka Command Prompt, ketik:
   ```bash
   git --version
   ```
   Harus keluar versi git (e.g., `git version 2.42.0`)

**Mac/Linux:**
Biasanya sudah installed. Verify:
```bash
git --version
```

### Step 3: Install Node.js (Optional tapi Recommended)
Node.js punya NPM, berguna untuk manage dependencies nanti.

1. Download dari https://nodejs.org (ambil LTS)
2. Install biasa
3. Verify:
   ```bash
   node --version
   npm --version
   ```

---

## B. Setup Project di VSCode

### Step 1: Buat Folder Project

```bash
# Buka Terminal/Command Prompt

# Navigate ke lokasi yang aman (Desktop, Documents, etc)
cd Desktop

# Buat folder project
mkdir koperasi-mahasiswa
cd koperasi-mahasiswa
```

### Step 2: Buka Folder di VSCode

**Opsi 1: Via Command Line**
```bash
code .
```
(Dot = buka folder sekarang)

**Opsi 2: Via GUI**
1. Buka VSCode
2. File → Open Folder
3. Pilih folder `koperasi-mahasiswa` yang baru dibuat
4. Click "Select Folder"

### Step 3: Copy File ke Folder

Copy 3 file yang sudah aku buatkan ke folder `koperasi-mahasiswa`:
- `koperasi.html` → Rename jadi `index.html`
- `vercel.json`
- `PANDUAN_DEPLOY_VERCEL.md` (untuk referensi)

**Cara copy:**
1. Download ketiga file dari chat ini
2. Copy ke folder `koperasi-mahasiswa`
3. Rename `koperasi.html` → `index.html`

Struktur folder seharusnya jadi:
```
koperasi-mahasiswa/
├── index.html
├── vercel.json
└── PANDUAN_DEPLOY_VERCEL.md
```

Di VSCode, di panel kiri ("Explorer") kamu harus lihat 3 file itu.

---

## C. Setup Git & GitHub

### Step 1: Initialize Git Repository

Di VSCode, buka Terminal (Ctrl+` atau View → Terminal)

Ketik perintah:
```bash
git init
git config user.name "Nama Kamu"
git config user.email "email@example.com"
git add .
git commit -m "Initial commit - Koperasi Mahasiswa Online"
```

Atau gunakan VSCode Git GUI:
1. Click icon Source Control (di sidebar kiri, ikon cabang)
2. Click "Initialize Repository"
3. Stage files (click + di samping filename)
4. Ketik message: "Initial commit - Koperasi Mahasiswa Online"
5. Click checkmark (Commit)

### Step 2: Buat Repository GitHub

1. Buka https://github.com/signup (jika belum punya akun)
2. Login ke GitHub
3. Click "+" → "New repository"
4. Nama: `koperasi-mahasiswa`
5. Visibility: **Public** (penting! agar Vercel bisa akses)
6. Jangan pilih README/License untuk sekarang
7. Click "Create repository"

### Step 3: Push ke GitHub

Setelah repository dibuat, GitHub kasih instructions. Ikuti yang "…or push an existing repository":

Di VSCode Terminal, ketik:
```bash
git branch -M main
git remote add origin https://github.com/USERNAME/koperasi-mahasiswa.git
git push -u origin main
```

**Ganti USERNAME dengan username GitHub kamu!**

Contoh:
```bash
git remote add origin https://github.com/ratih-dian/koperasi-mahasiswa.git
```

### Step 4: Verify

Buka https://github.com/USERNAME/koperasi-mahasiswa

Harus lihat 3 file:
- `index.html`
- `vercel.json`
- `PANDUAN_DEPLOY_VERCEL.md`

✅ Berhasil! Repository siap.

---

## D. Deploy ke Vercel

### Step 1: Daftar Vercel

1. Buka https://vercel.com/signup
2. Click "Continue with GitHub"
3. Authorize Vercel untuk akses GitHub kamu

### Step 2: Import Project

1. Dashboard Vercel → "New Project" / "Add New..."
2. Di "Import Git Repository", search `koperasi-mahasiswa`
3. Click repository kamu
4. Settings page akan muncul:
   - Framework: `Other` (atau skip)
   - Root Directory: `.` (atau kosongkan)
   - Environment Variables: (skip)
5. Click "Deploy"

### Step 3: Wait...

Vercel akan:
1. Fetch code dari GitHub
2. Build project
3. Deploy ke server

Dalam 1-2 menit, kamu dapat status "Success!" dan URL live.

URL bakal kayak gini:
```
https://koperasi-mahasiswa.vercel.app
```

Copy & test di browser!

---

## E. Edit & Update Website

### Workflow untuk update:

**Di VSCode:**
1. Edit `index.html` (atau file lain)
2. Save (Ctrl+S)
3. Buka Terminal: `Ctrl+` `
4. Ketik:
   ```bash
   git add .
   git commit -m "Update: deskripsi perubahan"
   git push
   ```

**Di Vercel:**
- Otomatis detect push ke GitHub
- Auto-build & deploy dalam ~1 menit
- Check status di Vercel Dashboard

Setiap kali push, Vercel otomatis redeploy. Cool, kan? 😎

---

## F. Useful VSCode Extensions

Install extensions buat productivity:

1. **Live Server** (Ritwick Dey)
   - Test HTML locally sebelum push
   - Right-click `index.html` → "Open with Live Server"
   - Auto-refresh pas kamu edit

2. **GitHub Copilot** (Optional, GitHub)
   - AI autocomplete
   - Bagus untuk learning

3. **Prettier** (Prettier)
   - Auto-format code
   - Settings → Format on Save

Cara install:
- Click Extensions (icon di sidebar)
- Search nama extension
- Click Install

---

## G. Troubleshooting

| Problem | Solusi |
|---------|--------|
| "git: command not found" | Install Git dari git-scm.com |
| "Cannot push to GitHub" | Check credentials, atau authenticate via token (Settings → Developer Settings → Personal Access Tokens) |
| Deploy failed di Vercel | Check logs di Vercel Dashboard → Deployments → Failed build → View logs |
| Website hilang data | Refresh browser atau coba incognito mode (localStorage issue) |
| File tidak muncul di GitHub | Make sure `git add .` sebelum commit |
| Vercel takes >5 min | Normal kalo project besar; biasanya 1-2 min untuk project sederhana |

---

## H. Next Steps

### After successful deploy:

1. **Share URL** ke teman-teman
2. **Customize produk**:
   - Edit `index.html`
   - Ubah produk sesuai inventory koperasi
   - Update harga
   - Ganti emoji dengan gambar (nanti bisa)

3. **Upgrade features**:
   - Add payment gateway (Midtrans)
   - Add user login/authentication
   - Add real database (Firebase/Supabase)

### Want to make changes later?

Just edit in VSCode → commit → push → auto-deploy!

---

## I. Git/GitHub Cheat Sheet

```bash
# Check status
git status

# Add all changes
git add .

# Commit with message
git commit -m "What changed"

# Push to GitHub
git push

# Pull latest from GitHub (if working with team)
git pull

# Check commit history
git log

# Undo last commit (jangan-jangan)
git reset HEAD~1

# Switch branch
git checkout -b nama-branch
```

---

## 🎉 Selesai!

Sekarang kamu punya:
- ✅ Local project di VSCode
- ✅ Repository di GitHub
- ✅ Live website di Vercel
- ✅ Auto-deploy workflow

Setiap kali `git push`, website auto-update. Professional banget! 🚀

---

**Need help?**
- **Git**: https://git-scm.com/doc
- **VSCode**: https://code.visualstudio.com/docs
- **Vercel**: https://vercel.com/docs
- **GitHub**: https://docs.github.com

Good luck! 💪
