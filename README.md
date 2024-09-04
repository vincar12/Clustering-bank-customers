# Model Klasifikasi Prediksi Bangkrut

### 1. Project Overview
Tujuan dari proyek ini adalah untuk membuat model clustering menggunakan K-Means untuk membagi data ke dalam segmen-segmen berdasarkan data kartu kredit 6 bulan terakhir.

---

### 2. Project Structure
```bash
├── P1G6_Set_1_Vincar.ipynb            # Jupyter notebook untuk analisis dan pembuatan model
├── P1G6_Set_1_Vincar_Inference.ipynb  # Jupyter notebook untuk inferensi model
├── P1G6_Set_1_Vincar.csv              # Dataset asli
├── data_inf.csv                       # Dataset inferensi
├── list_cols.txt                      # List kolom untuk inferensi
├── model.pkl                          # Penyimpanan model
├── pca.pkl                            # Penyimpanan PCA
├── scaler.pkl                         # Penyimpanan Scaler
├── README.md                          # Project README file
```

---

### 3. Workflow

1. **Query SQL**:
   - Data asli diambil menggunakan query dan diunduh sebagai csv.

2. **Data Loading**:
   - Data dimuat dalam pandas dataframe dari csv.
   
3. **Exploratory Data Analysis (EDA)**:
   - Eksplorasi data dengan tujuan memahami dataset lebih lanjut

4. **Feature Engineering**: Proses dengan tujuan modifikasi data agar dapat diproses oleh model.
   - **Missing Value Handling**: Analisa data missing
   - **Cardinality**: Cek kardinalitas atau nilai unik dari dataset, kardinalitas rendah biasanya menandakan data kategorikal alih-alih numerik
   - **Handling Outlier**: Handling data *outlier* dengan menghitung skew dan menggunakan *Z-Score* atau *Tukey's Rule*; lalu dilakukan *capping* dengan *winsorizer*
   - **Scaling, Dimension Reduction**: *Scaling* berfungsi menyetarakan angka-angka dalam data agar berada dalam sat skala yang sama. Lalu reduksi dimensi atau PCA digunakan agar model menggunakan fitur yang tidak terlalu banyak untuk mengurangi kemungkinan overfitting.

5. **Model Definition**:
   - Clustering menggunakan K-Means, mencari jumlah cluster yang tepat untuk dataset berdasarkan elbow method dan silhouette score.

6. **Model Training**:
   - Setelah menentukan jumlah cluster yang optimal, dilakukan training pada model berdasarkan parameter tersebut.

7. **Cluster Analysis**:
   - Analisis hasil clustering dengan melihat ciri-ciri tiap cluster yang membedakan satu cluster dengan cluster lain.

8. **Model Saving**:
   - Menyimpan model dengan pickle agar dapat digunakan pada data inference.
     
9. **Kesimpulan & Rekomendasi**:
   - Berisi kesimpulan dari proyek ini serta rekomendasi bisnis berdasarkan model yang dibuat.

10. **Inference**:
    - Dilakukan dalam notebook yang terpisah untuk mengurangi kemungkinan kebocoran data.

---

### 4. Hasil dan Kesimpulan
Dengan menggunakan metode PCA dan K-Means, ditemukan bahwa 5 cluster merupakan pembagian cluster yang optimal untuk dataset. Setelah dataset terbagi menjadi 5 cluster, kemudian dilakukan analisis tiap cluster untuk menemukan ciri-ciri yang menggambarkan cluster tersebut. Hasil dari analisis membagi cluster menjadi:
1. 'Kelas Menengah, Transaksi Tinggi'; data dalam cluster ini memiliki ciri tabungan dengan jumlah moderat, aktifitas finansial tinggi, serta penggunaan metode cicilan yang tinggi.
2. 'Kelas Atas, Transaksi Tinggi'; data dalam cluster ini memiliki ciri tabungan dengan jumlah tinggi, aktifitas finansial tinggi juga, dan penggunaan metode cicilan yang cukup tinggi.
3. 'Kelas Menengah, Transaksi Rendah'; data dalam cluster ini berciri memiliki tabungan dengan jumlah menengah, namun dengan aktifitas finansial yang rendah, sehingga uang tetap dalam tabungan.
4. 'Kelas Menengah Kebawah, Transaksi Moderat'; data dalam cluster ini berciri memiliki tabungan dengan jumlah cukup rendah, dengan aktifitas finansial yang cukup relatif dengan jumlah tabungan, serta penggunaan uang tunai yang lebih tinggi.
5. 'Kelas Atas, Transaksi Rendah'; data dalam cluster ini memiliki ciri tabungan tertinggi, namun aktifitas finansial sangat rendah. Kebanyakan aktifitas finansial berasal dari tarikan tunai.

Berdasarkan kesimpulan di atas dapat direkomendasikan beberapa hal:
- Untuk meningkatkan penggunaan bagi cluster dengan aktifitas finansial tinggi, dapat dibuat program loyalitas. Dimana semakin sering transaksi, terkumpul poin-poin loyalitas semakin besar dan semakin banyak benefit yang didapat.
- Untuk segmen menengah dengan aktifitas finansial rendah, perlu dibuat program dimana terlihat jelas keuntungan menggunakan kartu kredit dengan insentif yang menarik. Contohnya program-program diskon pada restoran atau bioskop.
- Sementara cluster atas dengan aktifitas rendah, dapat dilakukan hal yang sama berupa program insentif namun dengan insentif yang sesuai kelasnya. Seperti halnya diskon atau benefit dengan maskapai penerbangan untuk harga tiket, fasilitas, maupun atau pengumpulan poin maskapai tersebut.

---

### 5. References
- Dataset: Hacktiv8 Dataset `ftds-hacktiv8-project.phase1_ftds_018_hck.credit-card-information`
- Tools: Python, Pandas, NumPy, Seaborn, Matplotlib, Plotly, Scikit-Learn, Pickle.
