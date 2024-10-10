# Zer0x
Find bug
Menemukan kerentanan pada sebuah website memerlukan pendekatan yang sistematis dan pemahaman mendalam tentang berbagai jenis kerentanan yang bisa dieksploitasi. Berikut adalah beberapa langkah umum yang bisa kamu ikuti untuk menemukan kerentanan pada sebuah website:

# 1. Pengenalan Target

Sebelum memulai, penting untuk memahami teknologi yang digunakan oleh website tersebut. Beberapa hal yang perlu diperhatikan:

Framework: Django, Laravel, Express.js, dll.

Bahasa: PHP, Python, Ruby, JavaScript, dll.

Server: Apache, Nginx, IIS, dll.

Basis data: MySQL, PostgreSQL, MongoDB, dll.


Tools: WhatWeb, Wappalyzer.

# 2. Pengumpulan Informasi (Reconnaissance)

Pengumpulan informasi sangat penting untuk mengetahui struktur website, endpoint yang ada, dan teknologi yang digunakan. Langkah-langkah umum meliputi:

DNS Enumeration: Mengidentifikasi subdomain yang bisa diakses.

WHOIS Lookup: Mengetahui informasi domain.

Crawler Website: Menggunakan tools untuk memetakan semua URL yang ada.


Tools: Sublist3r, Amass, Burp Suite, dirsearch, GoBuster.

# 3. Analisis Permukaan Serangan

Analisis permukaan serangan berarti mengevaluasi semua endpoint dan komponen website yang bisa menjadi pintu masuk serangan. Periksa fitur seperti:

Form input

Parameter URL

API Endpoint


Tools: Burp Suite, Postman, Nuclei, OWASP ZAP.

# 4. Pengujian Kerentanan Umum

Setelah mengenali permukaan serangan, berikut beberapa kerentanan umum yang dapat diuji:

a. SQL Injection (SQLi) Kerentanan ini terjadi jika input dari pengguna digunakan dalam query SQL tanpa sanitasi yang tepat.

Payload: ' OR 1=1 -- (untuk login bypass)

Tools: sqlmap, Burp Suite Intruder

Contoh Percobaan: Tes di parameter yang berinteraksi dengan database seperti /search?q=.


b. Cross-Site Scripting (XSS) Terjadi ketika input pengguna tidak disanitasi dan disisipkan langsung ke halaman web.

Payload: <script>alert(1)</script>

Tools: XSS Hunter, Burp Suite

Contoh Percobaan: Tes di semua input yang akan ditampilkan kembali di halaman.


c. Insecure Direct Object Reference (IDOR) Ini adalah ketika pengguna bisa mengakses data milik pengguna lain dengan mengubah ID atau parameter.

Payload: Coba ganti ID pada URL, misalnya dari /user/123 menjadi /user/124.

Tools: Burp Suite, Postman


d. Server-Side Template Injection (SSTI) Ketika aplikasi menggunakan template engine yang tidak aman untuk memproses input pengguna.

Payload: {{7*7}} atau ${{7*7}}

Tools: Manual testing dengan template engine seperti Jinja2, Twig, dll.

Contoh Percobaan: Tes input yang diproses di backend.


e. Cross-Site Request Forgery (CSRF) CSRF memungkinkan penyerang untuk membuat korban melakukan aksi yang tidak diinginkan pada website.

Payload: Coba buat permintaan POST dengan token yang tidak sah.

Tools: Burp Suite CSRF POC generator


# 5. Automasi Pengujian dengan Tools

Untuk mempercepat proses, kamu bisa menggunakan berbagai tools otomasi seperti:

Nuclei: Untuk menjalankan template kerentanan umum.

Burp Suite Intruder: Untuk brute-forcing atau fuzzing input.

OWASP ZAP: Untuk scanning kerentanan secara otomatis.


# 6. Menguji dengan Payload Khusus

Setelah kamu menemukan titik potensi kerentanan, uji dengan payload yang lebih spesifik. Misalnya:

Untuk XSS: Tes dengan payload lebih kompleks seperti "><svg onload=alert(1)>.

Untuk SQLi: Gunakan berbagai teknik seperti UNION-based SQLi atau Error-based SQLi dengan payload seperti ' UNION SELECT NULL,@@version--.


# 7. Membaca Log dan Respon

Perhatikan respon server untuk menemukan petunjuk apakah website rentan atau tidak. Misalnya:

Untuk SQLi, jika muncul pesan error seperti You have an error in your SQL syntax.

Untuk XSS, jika alert(1) muncul di halaman.


# 8. Laporan dan Dokumentasi

Setelah menemukan kerentanan, penting untuk mendokumentasikannya dengan jelas, termasuk:

Deskripsi kerentanan.

Langkah-langkah eksploitasi.

Payload yang digunakan.

Respon dari server.


Dengan mengikuti langkah-langkah di atas dan menggunakan tools yang tepat, kamu bisa menemukan berbagai kerentanan dalam sebuah website dan mengoptimalkan peluangmu dalam program bug bounty.

