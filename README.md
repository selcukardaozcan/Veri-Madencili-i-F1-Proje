# Veri-Madenciliği-F1-Proje (WEKA)
Proje, 2025 F1 verileriyle regresyon ve karar ağacı modelleriyle yarış puanlarını tahmin etmeyi amaçlar.

🏎️ Formula 1 Analizi: Başlangıç Pozisyonu Puanı Nasıl Etkiler?
(2025 Sezonu)Bu çalışma, hazırladığım bir veri madenciliği projesidir.
2025 F1 sezonu verilerini kullanarak, bir pilotun yarışa başladığı sıranın (Starting Grid) yarış sonu kazandığı puan (Points) üzerindeki etkisini modelledim.



📊 Veri Seti ve HazırlıkAnalizde 24 farklı Grand Prix'den 419 satırlık güncel bir veri seti kullandım.

Öznitelikler:Pist ismi, Takım, Sürücü ve Başlangıç Sırası.

Hedef: Yarış sonunda alınan 0-25 arası puan.

Temizlik: Modelin verimliliğini düşürmemesi için yarışı tamamlayamayan (DNF) veya diskalifiye edilen (DSQ) veriler ayıklandı.


🔍 Kritik Bulgular: WEKA üzerinde yaptığım CorrelationAttributeEval analizi sonucunda, puanı belirleyen en güçlü faktörün -0.7384 skorla Starting_Grid olduğu bilimsel olarak kanıtlanmıştır. 

Negatif korelasyon, başlangıç sırası rakamı küçüldükçe (yani önde başladıkça) alınan puanın arttığını doğrular.

🤖 Algoritma Karşılaştırmaları: Projeyi 5 farklı makine öğrenmesi algoritması ile test ettim. 

İşte çapraz doğrulama (Cross-validation) sonuçları: Korelasyon KatsayısıMAE (Hata Oranı)Random Forest0.83292.7289IBk (KNN, K=3)0.83252.7553Linear Regression0.83632.9263M5P0.85502.7448


Not: Tablo verileri çapraz doğrulama (folds 10) sonuçlarına dayanmaktadır.

💡 Neden Random Forest ve IBk Daha Başarılı?Lineer regresyon modelleri, F1'in "10. sıradan sonra herkes 0 puan alır" kuralını (0'da sabitlenme) tam olarak anlayamaz ve negatif puan tahminleri üretebilir.

IBk (KNN), geçmişteki en yakın 3 yarışın ortalamasını aldığı için gerçekçi bir 0-25 aralığında kalır.Random Forest, 100 farklı ağaç kullanarak F1'in basamaklı puan yapısını (25-18-15...) düz bir çizgiden çok daha iyi yakalar.


🛠️ Nasıl Kullanılır?Veri setini .arff formatında WEKA'ya yükleyin.Starting_Grid ve Points özniteliklerini numeric olarak ayarlayın.Özellikle podyum adayları için M5P ağacını görselleştirerek karar düğümlerini inceleyin.

👤 Hazırlayan: Selçuk Arda Özcan ,

[Veri Seti](https://www.kaggle.com/datasets/selcukardaozcan/f1-2025-season-grand-prix-results-withs-points) , 

[Kaggle Profilim](https://www.kaggle.com/selcukardaozcan) ,

Lisans: Ticari olmayan (Non-commercial) kullanım içindir.
