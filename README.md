## Claim Insurance Predictions (Travel Insurance)
#### Created By : Syahid Ahmad Mukrim

### Background :
Travel insurance / Asuransi perjalanan adalah jenis asuransi yang memberikan perlindungan terhadap berbagai risiko saat kita melakukan perjalanan baik di dalam negeri maupun ke luar negeri. Beberapa risiko yang dilindungi seperti, keterlambatan atau pembatalan penerbangan, bagasi hilang, kejadian medis dan hal lainnya sesuai polis asuransi yang kita pilih. Jumlah premi yang dibayarkan bergantung dengan berbagai faktor seperti tujuan perjalanan, durasi perjalanan, usia pemegang polis, dan cakupan yang dipilih.

Perusahaan asuransi perjalanan harus memastikan kestabilan keuangan perusahaan terhadap premi yang dikumpulkan. Pertama, premi tersebut digunakan untuk membentuk dana klaim, yaitu dana yang disisihkan untuk membayar klaim yang diajukan oleh pemegang polis jika terjadi kejadian tak terduga selama perjalanan. Kedua, sebagian premi juga diinvestasikan oleh perusahaan asuransi untuk menghasilkan pendapatan tambahan. Investasi ini membantu mengimbangi biaya klaim dan meningkatkan keuntungan perusahaan. Premi juga digunakan untuk menutupi biaya operasional perusahaan yang terkait dengan menyediakan layanan travel insurance kepada pemegang polis. Dengan mengelola premi dengan baik, perusahaan asuransi dapat memastikan bahwa mereka memiliki dana yang cukup untuk membayar klaim, menjaga kestabilan keuangan, dan memberikan perlindungan yang dijanjikan kepada pemegang polis.

### Problem Statement :

Perusahaan asuransi perjalanan ingin meningkatkan efisiensi perencanaan dana pertanggungan dengan memprediksi kemungkinan seorang pemegang polis akan mengajukan klaim atau tidak. Dengan perencanaan dana yang tepat, perusahaan dapat menjaga kredibilitas melalui proses klaim yang lancar dan mengurangi risiko dana tidak terpakai akibat rendahnya jumlah pemegang polis yang mengajukan klaim.

### Goals :

Maka berdasarkan permasalahan tersebut, perusahaan ingin memiliki kemampuan untuk memprediksi kemungkinan seorang pemegang polis apakah akan mengajukan klaim atau tidak. Sehingga dapat memperkirakan dengan cara:

Mengembangkan model prediksi yang dapat memperkirakan probabilitas pemegang polis mengajukan klaim asuransi. Dengan memperkirakan klaim potensial dengan akurat, Departemen keuangan dapat mengalokasikan dana asuransi secara tepat, memastikan dana yang cukup tersedia untuk menutupi klaim yang diharapkan sambil meminimalkan risiko dana tidak terpakai.
Mengetahui faktor yang mempengaruhi pemegang polish untuk melakukan klaim
Stakeholder : Departemen Keuangan ( Departemen Keuangan bertanggung jawab untuk mengelola aspek keuangan perusahaan secara keseluruhan. Mereka dapat terlibat dalam mengelola premi yang dikumpulkan, mengalokasikan dana untuk dana klaim, mengelola investasi, dan memantau kesehatan keuangan perusahaan. )

### Analytic Approach :

Jadi yang akan kita lakukan adalah menganalisis data untuk menemukan pola yang membedakan pemegang polis yang akan melakukan klaim atau tidak berdasarkan variabel yang ada. Kemudian kita akan membangun model klasifikasi yang akan membantu perusahaan untuk dapat memprediksi probabilitas seorang pemegang polis akan mengajukan klaim atau tidak berdasarkan riwayat data sebelumnya.

### Target (Claim) :

0 (No) : Tidak Melakukan Klaim

1 (Yes) : Melakukan Klaim

### Metric Evaluation :

TP : Jumlah pemegang polis yang memang benar melakukan klaim

TN : Jumlah pemegang polis yang memang benar tidak melakukan klaim

Type of Error:

Type 1 erorr (FP) : False Positive ( Pemegang polis diprediksi melakukan klaim, padahal aktualnya tidak melakukan klaim )
Konsekuensi: Dana klaim tidak terpakai(idle money), dana yang seharusnya dapat dimaksimalkan untuk investasi atau biaya operasional perusahaan

Type 2 error (FN) : False Negative ( Pemegang polis diprediksi tidak melakukan klaim, padahal aktualnya mengajukan klaim)
Konsekuensi: Perusahaan perlu mengeluarkan dana yang tidak terduga untuk memenuhi claim pemegang polis. Hal tersebut dapat mengganggu proses klaim pelanggan sehingga kredibilitas perusahaan dapat berkurang

Berdasarkan konsekuensinya, maka sebisa mungkin yang akan kita lakukan adalah membuat model yang harus mempertimbangkan Type Error 1 (False Positive) dan Type Error 2 (False Negative). Jadi nanti metric utama yang akan kita gunakan adalah balanced accuracy dibandingkan accuracy biasa karena terdapat highly imbalanced (98.2% dan 1.8% ) pada data target claim ( Balanced Accuracy: When Should You Use It? ).

### Conclusion: 

Secara kesuluruhan, model memiliki kemampuan klasifikasi cukup baik dalam memprediksi dengan benar baik pemegang polis yang mengajukan klaim maupun yang tidak mengajukan klaim dengan melihat balanced_accuracy dan nilai ROC_AUC sebesar 76.8 %. Model dapat mengetahui 82 % pemegang polis yang tidak melakukan klaim dan 72% pemegang polis yang akan melakukan klaim (berdasarkan recall). Namun, model cukup berjuang dalam memprediksi dengan jumlah yang tepat pemegang polis yang akan melakukan klaim sebesar 6.4% (berdasarkan precision) dikarenakan dataset sangat imbalanced. Tetapi, hal tersebut tidak apa-apa karena menjadi titik aman bagaimana nantinya perusahaan dalam menangani pemegang polis yang akan melakukan klaim.

Berdasarkan analisa faktor yang berpengaruh terhadap pemegang polis melakukan klaim, faktor - faktornya adalah Agensi yang dipilih, channel distribusi, dan Net Sales yang diterima perusahaan (berdasarkan feature importance).

Berdasarkan contoh hitungan pada business overview, terlihat bahwa dengan menggunakan model, perusahaan dapat mengoptimalkan biaya klaim yang tidak terpakai sebesar 38% dengan cara mendistribusikannya untuk biaya operasional dan investasi.

### Recommendation:

Adapun beberapa rekomendasi yang dapat diberikan terkait sisi model dan bisnis:

Model:
- Saat penarikan data, memastikan data yang didapat tidak ada missing value pada variabel gender
- Penambahan data historis yang lebih lama, terutama pemegang polis yang melakukan klaim agar mengurangi imbalance data yang signifikan
- Adanya kolom dengan fitur lain yang berhubungan dengan status klaim seperti ID pemegang polis, waktu pemesanan produk asuransi agar saat data cleaning lebih subjektif
- Model dapat ditingkatkan dengan melakukan tuning hyperparameter dengan nilai yang sudah didapat sebagai referensi dan menambahkan parameter lain
- Pemilihan teknik resampling lain yang belum digunakan seperti ADASYN (Adaptive Synthetic)

Bisnis:
- Pada dana yang disiapkan untuk pertanggungan klaim, sebagian dapat diinvestasikan juga pada platform yang dapat diambil dengan cepat (< dari waktu pencairan polis). Sehingga, dapat diambil sewaktu-waktu dibutuhkan dengan cepat. Namun, perlu dianalisa resikonya lebih lanjut.
- Maksimalkan sebagian biaya operasional untuk menambah customer travel insurance, dikarenakan berdasarkan data historis hanya 2% yang melakukan klaim dibandingkan 98% yang tidak melakukan klaim. Hal tersebut menandakan bahwa bisnis ini berjalan sangat baik dan menguntungkan.
- Menggunakan model machine learning yang telah dibuat sebagai pertimbangan solusi untuk menentukan proporsi dana untuk klaim, biaya operasional dan investasi. Tentunya dibutuhkan analisis dan evaluasi lebih mendalam untuk penerapannya
- Menganalisa data-data yang model kita masih salah tebak untuk mengetahui alasannya dan karakteristiknya bagaimana.
