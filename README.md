[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=8996664&assignment_repo_type=AssignmentRepo)
_Graded Challenge ini dibuat guna mengevaluasi pembelajaran pada Hacktiv8 Data Science Fulltime Program khususnya pada Business Knowledge & SQL Query._

---

## Dataset Description

* Pada graded challenge ini, data diakses menggunakan `bigquery-public-data` pada Google Cloud Big Query.
* Buka [Google Cloud Platform](https://console.cloud.google.com/), masuk ke BigQuery, lalu buka tab `bigquery-public-data` atau klik link [berikut](https://console.cloud.google.com/bigquery?p=bigquery-public-data&d=samples&page=dataset&_ga=2.245085957.1471931019.1642739417-486643658.1638156099).
**WAJIB GUNAKAN GOOGLE COLAB**

```{attention}
Perhatikan petunjuk penggunaan dataset!
```

1. Gunakan database `thelook_ecommerce`.
2. Koneksikan `BigQuery` kamu ke Google Colab tempat kamu mengerjakan P0-GC3 dengan code berikut:

```
from google.colab import auth
auth.authenticate_user()
print('Authenticated')

project_id = "rock-wonder-317907" #GUNAKAN GCP PROJECT-ID KALIAN MASING-MASING
client = bigquery.Client(project=project_id)
```
3. Untuk melakukan Query menggunakan skema ini, kamu dapat menggunakan method `client.query('Masukkan Querynya').to_dataframe()`. Outputnya akan berupa Pandas dataframe, sehingga harus import Pandas. Contoh:
```
df = client.query('''
SELECT extract(year from created_at) as year, extract(month from created_at) as month, count(order_id) as sales
FROM `bigquery-public-data.thelook_ecommerce.orders`
WHERE status='Shipped' and created_at<"2022-07-01"
GROUP BY year,month
ORDER BY year,month ASC
''').to_dataframe()
```


## Assignment Problems

Kamu adalah seorang data analis di The Look yang merupakan salah satu platform e-commerce terbesar di planet Mars. Kamu diminta untuk membuat laporan evaluasi aktivitas penjualan di platform tersebut.

Untuk mempermudah pekerjaan kamu supaya terarah, kamu harus menentukan problem statement dengan success criteria berdasarkan SMART. Namun tantangannya, kamu tentukan problem statement berdasarkan penjabaran-penjabaran analisis dalam bentuk persoalan yang harus kamu jawab menggunakan Query SQL. (SMART akan berdasarkan dari poin-poin penjabaran).

***Catatan:*** *Tidak perlu membuat plot/visualisasi data. Cukup tampilkan dataframe!*

**Poin penjabaran:**

1. Berapa jumlah transaksi yang berstatus `Complete` tiap bulan selama Q1 sampai Q3 di tahun 2022? Insight apa yang bisa kamu berikan?
2. Berikan informasi total penjualan (dalam USD) tiap bulan selama Q1 sampai Q3 di tahun 2022! (Hanya yang transaksi berstatus `Complete`. Apa informasi yang bisa kamu sampaikan?
3. Berapa user yang melakukan transaksi berstatus `Complete` di tiap bulan dari Q1 sampai Q3 2022? Apa kesimpulanmu?
4. Kategori produk apa saja yang paling banyak dibeli (staus transaksi: `Complete`) di tiap bulannya selama Q1 sampai Q3 tahun 2022? Berikan insight!
5. Kategori produk apa saja yang paling banyak mendapatkan pendapatan (staus transaksi: `Complete`) di tiap bulannya selama Q1 sampai Q3 tahun 2022? Berikan insight!
6. Dibandingkan dengan jumlah transaksi dan total penjualan, mana yang paling berkaitan dengan jumlah user yang melakukan transaksi? Apa analisis yang dapat kamu jelaskan? (_Hint: Kamu bisa menggunakan korelasi_)

**PERHATIAN!**. Untuk semua penjabaran tidak boleh menggunakan bantuan Pandas Query atau method lainnya untuk menyeleksi, menggabungkan, memanipulasi data. HANYA gunakan Query SQL. Tidak perlu menampilkan grafik, hanya berupa dataframe.

**POIN ANALISIS**
1. Berikan kesimpulan dari laporan/informasi yang dibuat berdasarkan problem statement/poin penjabaran menggunakan bahasa awam! (boleh dalam beberapa paragraf)

**POIN PERTANYAAN**
1. Apakah problem statement yang kamu definisikan di awal dapat terukur ketercapaiannya? berikan pendapatmu!
2. Berdasarkan hasil analisis yang sudah kamu lakukan dari 6 penjabaran di atas, jika CEO perusahaanmu ingin menargetkan pendapatan di awal kuartal 4 harus mencapai $250000, apakah masuk akal?
3. CEO kamu menargetkan di kuartal 4 ada investor yang dapat menyuntikan dana ke perusahaanmu, dimana investor akan melihat GMV selama 3 kuartal terakhir serta prospek kedepan minimal di kuartal 4 akan seperti apa. Berikan informasi kepada CEO mu berdasarkan trend transaksi, jumlah user yang bertransaksi, dan GMV 3 kuartal terakhir, apakah perusahaanmu layak atau tidak mendapatkan investor baru!

## Assignment Submission

- Simpan assignment pada sesi ini dengan nama `h8dsft_P0W3_<nama-student>.ipynb`, misal `h8dsft_P0W3_raka_ardhi.ipynb`.
- Push Assigment yang telah kalian buat ke akun Github masing-masing student.

## Assignment Objectives

*Graded Challenge 3* ini dibuat guna mengevaluasi Business Knowledge dan SQL:

- Mampu memperoleh data menggunakan BigQuery
- Mampu melakukan pemrosesan data sebelum melakukan perhitungan dan analisa
- Mampu menerapkan konsep statistics pada persoalan
- Memahami dasar Pengetahuan Bisnis

---

## Assignment Rubrics

### Code Review

| Criteria | Meet Expectations | Points |
| --- | --- | --- |
| SQL Queries | Mampu memperoleh data menggunakan SQL BigQuery, melingkupi kesesuaian kode dengan tabel yang dihasilkan | (5 each) 25 pts |
| Statistical Implementation | Mampu melakukan uji korelasi dengan code| 5 pts |


### Concepts

| Criteria | Meet Expectations | Points |
| --- | --- | --- |
| Problem Statement | Mampu mendefinisikan problem statement dengan success criteria menggunakan kerangka SMART | 5 pts |
| Business Acumen | Mampu menjawab pertanyaan dengan singkat, jelas, dan padat serta sesuai dengan konsep dan logika yang ada (5 each) | 15 pts |


### Analysis

| Criteria | Meet Expectations | Points |
| --- | --- | --- |
| Insights | Mampu memberikan kesimpulan/insight dari masing-masing penjabaran | 5 each (30 pts max) |
| Overall Analysis | Mampu memberikan kesimpulan/insight dari penjabaran dan problem statement pada poin analisis | 10 pts |


### Readability

| Criteria | Meet Expectations | Points |
| --- | --- | --- |
| Tertata Dengan Baik | Semua baris kode terdokumentasi dengan baik dengan menggunakan Markdown untuk penjelasan kode. | 10 pts |

---

```
Total Points : 100
```

## Score Reduction

Pengurangan poin akan diberlakukan jika Student terlambat mengumpulkan tugas yang telah diberikan. Adapun besarnya pengurangan adalah :

| Criteria | Max Points GC3 |
| --- | --- |
| Keterlambatan kurang dari 1 jam setelah deadline | 75 pts (75 %) |
| Keterlambatan lebih dari 1 jam - 1 hari setelah deadline | 50 pts (50 %) |
| Keterlambatan lebih dari 1 hari setelah deadline | 0 pts (0 %) |
