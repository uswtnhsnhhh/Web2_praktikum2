# 📘 Praktikum 2 - Database, Model, dan Menampilkan Artikel CodeIgniter 4

## 👤 Data Mahasiswa

* Nama: **Uswatun Hasanah**
* NIM: **312410163**
* Kelas: **I241A**

---

## 🎯 Tujuan Praktikum

Praktikum ini bertujuan untuk:

* Membuat database MySQL
* Menghubungkan CodeIgniter ke database
* Membuat model
* Menampilkan data artikel dari database
* Menggunakan template view

---
## Tahapan Pengerjaan

1. Membuat Database
   Masuk ke MySQL:
   ```
   /opt/lampp/bin/mysql -u root
   ```
   Membuat Database:
   ```
   CREATE DATABASE lab_ci4;
   USE lab_ci4;
   ```
   Membuat tabel artikel:
   ```
   CREATE TABLE artikel (
    id INT(11) auto_increment,
    judul VARCHAR(200) NOT NULL,
    isi TEXT,
    gambar VARCHAR(200),
    status TINYINT(1) DEFAULT 0,
    slug VARCHAR(200),
    PRIMARY KEY(id)
    );
   ```
   Menambahkan data:
   ```
   INSERT INTO artikel (judul, isi, slug)
    VALUES
    ('Artikel 1', 'Isi artikel pertama', 'artikel-1'),
    ('Artikel 2', 'Isi artikel kedua', 'artikel-2');
   ```

2. Konfigurasi Database
   File:
   ```
   app/Config/Database.php
   ```
   Konfigurasi
   ```
   'hostname' => 'localhost',
    'username' => 'root',
    'password' => '',
    'database' => 'lab_ci4',
    'DBDriver' => 'MySQLi',
   ```

3. Membuat Model
   File:
   ```
   app/Models/ArtikelModel.php
   ```
   Isi Model:
   ```
   <?php

    namespace App\Models;

    use CodeIgniter\Model;

    class ArtikelModel extends Model
    {
    protected $table = 'artikel';
    protected $primaryKey = 'id';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['judul', 'isi', 'status', 'slug', 'gambar'];
    }
   ```

4. Membuat Controller Artikel
   File:
   ```
   app/Controllers/Artikel.php
   ```
   Isi:
   ```
   public function index()
    {
    $model = new \App\Models\ArtikelModel();
    $artikel = $model->findAll();

    return view('artikel/index', [
        'artikel' => $artikel,
        'title' => 'Daftar Artikel'
    ]);
    }
   ```

5. Membuat View Artikel
   File:
   ```
   app/Views/artikel/index.php
   ```
   Isi:
   ```
   <h1><?= $title; ?></h1>

    <?php foreach ($artikel as $row): ?>
    <h3><?= $row['judul']; ?></h3>
    <p><?= $row['isi']; ?></p>
    <hr>
    <?php endforeach; ?>
   ```

## Hasil Modul 2
Berhasil menampilkan daftar artikel dari database:

*Artikel 1
*Artikel 2

Tampilan website:

*Header
*Menu navigasi
*Daftar artikel
*Footer

URL akses:
```
http://localhost/lab11_php_ci/ci4/public/artikel
```

## Kesimpulan
Pada Modul 1 dan Modul 2 berhasil dilakukan instalasi CodeIgniter 4, pembuatan routing, controller, view, koneksi database, model, serta menampilkan data artikel dari database ke halaman website. Praktikum ini menjadi dasar untuk melanjutkan ke modul berikutnya seperti detail artikel dan CRUD (Create, Read, Update, Delete).

# Tampilan Artikel
(<img width="1366" height="768" alt="daftar artikel" src="https://github.com/user-attachments/assets/a3128674-5ae8-461a-9d50-4902d6cffe75" />

# Tampilan About
(<img width="1366" height="768" alt="halaman about web2" src="https://github.com/user-attachments/assets/a659ba77-13f2-49dc-acca-f76410181553" />

# Tampilan Contact
(<img width="1366" height="768" alt="halaman contact web2" src="https://github.com/user-attachments/assets/0035bf7b-9d02-4688-80ca-2303b6045edf" />

# Tampilan FAQ
(<img width="1366" height="768" alt="halaman faq web2" src="https://github.com/user-attachments/assets/addcda63-3be8-4f24-9e55-0518759fc335" />

# Tampilan Isi Artikel
(<img width="1366" height="768" alt="isi artikel web2" src="https://github.com/user-attachments/assets/c7a9f705-6f08-4530-80e6-da88e55fe09a" />
