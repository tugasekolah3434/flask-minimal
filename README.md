# flask-minimal

Proyek starter Flask minimal yang dirancang untuk membantu Anda menyiapkan aplikasi web yang bersih, sederhana, dan efisien dengan cepat. Proyek ini disusun agar tetap ringan dan fokus pada produktivitas, dengan semua kode Anda terkandung dalam satu file (app.py), bersama dengan template dasar dan aset statis.


## Fitur
-Aplikasi Flask dalam satu file (app.py) untuk memaksimalkan produktivitas dan kesederhanaan.
-Struktur template HTML dasar dengan styling dan JavaScript minimal.
-Pengaturan proyek yang sederhana dan intuitif tanpa kompleksitas yang tidak perlu.
-Mudah disesuaikan untuk pengembangan aplikasi web yang cepat.


## Persiapan
```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip -y
```

## Instalasi

1. Clone repository:
```bash
git clone https://github.com/yourusername/flask-minimal.git
cd flask-minimal
```

2. Buat virtual environment (disarankan):
```bash
python3 -m venv venv
source venv/bin/activate
```

3. Install dependensi yang diperlukan:
```bash
pip install -r requirements.txt
```

4. Jalankan aplikasi:
```bash
python app.py
```

   

Aplikasi Flask akan mulai berjalan, dan Anda dapat melihatnya dengan membuka http://localhost:5000 di browser Anda.


## Tambahan

Agar Flask-app otomatis berjalan setiap kali EC2 instance dinyalakan kita bisa menggunakan systemd, caranya :
1. Buat file service untuk systemd

```bash
sudo nano /etc/systemd/system/flask-app.service
```
Paste isi file service, sesuaikan path jika berbeda.
```
 [Unit]
Description=Flask Minimal App
After=network.target

[Service]
Type=simple
User=ubuntu
WorkingDirectory=/home/ubuntu/flask-minimal
Environment=PATH=/home/ubuntu/flask-minimal/venv/bin
ExecStart=/home/ubuntu/flask-minimal/venv/bin/python app.py
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

Aktifkan dan jalankan service

```bash
# Reload systemd
sudo systemctl daemon-reload

# Enable service (akan start otomatis saat boot)
sudo systemctl enable flask-app.service

# Start service sekarang
sudo systemctl start flask-app.service

# Cek status
sudo systemctl status flask-app.service
```

## Penggunaan

Proyek starter ini siap digunakan sebagai fondasi untuk membangun aplikasi web. File app.py berisi semua rute dan logika Flask, membuatnya mudah untuk diperluas dan disesuaikan. Anda dapat menambahkan lebih banyak template, rute, atau file statis sesuai kebutuhan.

## Kostumisasi
You can easily modify:

 - Struktur HTML di `templates/index.html`
 - Styling di `static/style.css`
 - Interaktivitas di `static/script.js`

Jangan ragu untuk memperbarui file app.py untuk menambahkan rute atau logika tambahan sesuai kebutuhan Anda.

## Lisensi
Proyek ini dilisensikan di bawah Lisensi MIT.

## Kontribusi
Jangan ragu untuk melakukan fork repository ini dan membuat pull request jika Anda memiliki perbaikan atau perbaikan bug. Jika Anda memiliki saran, buka issue, dan kita akan membahasnya!
Proyek ini dibangun dengan mempertimbangkan kesederhanaan dan efisiensi, sempurna untuk memulai aplikasi web kecil atau prototipe dengan overhead minimal.
