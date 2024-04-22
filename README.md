# Tutorial 8 (PUBLISHER)
Nama: Vina Myrnauli Abigail Siallagan<br>
NPM: 2206825776<br>
Kelas: Pemrograman Lanjut - A<br>

---
## REFLEKSI 

###### 1. How many data your publisher program will send to the message broker in one run?
* Program publisher akan mengirimkan lima set informasi ke dalam sistem pengirim pesan pada satu waktu.
* Penyebabnya adalah karena ada lima kali pemanggilan fungsi bernama `publish_event`. Setiap kali fungsi dipanggil, itu akan mengirim satu pesan yang berisi informasi tentang kejadian pembuatan pengguna atau `UserCreatedEventMessage` ke dalam sistem pengirim pesan.

###### 2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
* URL `amqp://guest:guest@localhost:5672` dipergunakan dalam kedua program subscriber dan publisher. Ini mengindikasikan bahwa kedua subscriber dan publisher terkoneksi ke server AMQP yang identik.
* Koneksi menggunakan informasi akun yang serupa, dengan nama pengguna "guest" dan sandi "guest". Server AMQP aktif di localhost menggunakan port 5672.

###### 3.  Running RabbitMQ as message broker
![Photo 1](images/photo1.png)

###### 4.  Sending and processing event
* Screenshot berhasilnya menerima 5 event message broker dari publisher pada terminal subscriber.
![Photo 3](images/photo3.png)

* Screenshot berhasilnya menjalankan `cargo run` untuk mengirim 5 event memalui message brocker yang akan diproses oleh subscriber pada terminal publisher.
![Photo 2](images/photo2.png)

###### 5. Monitoring chart based on publisher
Screenshot grafik antarmuka RabbitMQ yang menunjukkan adanya spike pada message rates karena menjalankan `cargo run` atau publisher berkali-kali. 
![Photo 4](images/photo4.png)

###### 6. Code repair
* Memperhatikan hasil dari `publish_event`: saat ini, hasil dari fungsi `publish_event` diabaikan dengan menggunakan _=. Disarankan untuk menangani hasil ini dengan lebih tepat untuk memastikan tidak ada potensi kesalahan yang terlewat.
* Refaktor pemanggilan fungsi: `publish_event` dipanggil beberapa kali dengan argumen yang serupa. Sebaiknya kode ini direfactor menjadi loop atau fungsi terpisah untuk mengurangi duplikasi dan meningkatkan kejelasan.
* Pengkodean langsung: koneksi string dan nama event dikodekan secara langsung di dalam kode. Lebih baik untuk memisahkan ini ke dalam file konfigurasi terpisah atau menggunakan environment variables untuk meningkatkan fleksibilitas dan keamanan.