# 🚛 Sürdürülebilir Atık Yönetimi İçin Çok Modlu Taşıma Ağı Optimizasyonu

## 📌 Proje Hakkında
Bu çalışma, Quebec eyaletindeki katı atık yönetim sisteminin lojistik verimliliğini ve çevresel sürdürülebilirliğini artırmak amacıyla çok modlu (karayolu ve denizyolu) bir taşıma ağı tasarımı önermektedir. 
Makalede yer alan veri seti yerine tarafımca veri seti oluşturulmuştur.

* Mevcut literatürdeki (Larbi et al., 2024) temel senaryolar (S1, S2, S3) incelenmiş ve bu senaryoların operasyonel gerçeklikten uzak varsayımları tespit edilmiştir. 
Bu eksiklikleri gidermek amacıyla, çalışmaya "Senaryo 4: Gerçekçi Operasyonel Model" eklenmiştir. 
Bu yeni senaryo, minimum gemi yükü, maksimum taşıma süresi, tesis güvenlik payları ve karbon vergisi gibi katı kısıtları matematiksel modele entegre etmektedir. 
* Python ve PuLP kütüphanesi kullanılarak yapılan optimizasyon sonuçları ve literatürde önerilen Senaryo 2 (S2), gemi doluluk oranlarını ve tesis risklerini ihmal ettiği için %14 maliyet avantajı vaat etse de operasyonel olarak risklidir. 
* Geliştirilen Senaryo 4 (S4), %90 Güvenlik Marjı ve 1000 Ton Min. Gemi Yükü kısıtları altında çalıştırıldığında, maliyetler %5 artsa da sistemin kırılganlığı (breakdown risk) minimize edilmiş ve uygulanabilir bir rota elde edilmiştir.

**Senaryo 1 (S1 - Karayolu Bazlı):** Mevcut durumu yansıtır. Tüm atıklar (Mavi Kutu ve İnşaat/Yıkım atıkları) belediyelerden tesislere sadece kamyonlarla taşınır. Amaç, finansal maliyeti minimize etmektir.
**Senaryo 2 (S2 - Çok Modlu):** Atıkların Endüstriyel Liman Bölgeleri (ZIP) üzerinden denizyolu ile taşınmasına izin verilir. Bu senaryo, denizyolunun düşük birim maliyetinden faydalanarak maliyetleri %14 oranında düşürmeyi hedefler.
**Senaryo 3 (S3 - Sürdürülebilir):** Amaç fonksiyonuna sadece finansal maliyetler değil, "Dışsal Maliyetler" (kaza, gürültü, hava kirliliği, trafik) de eklenir.
Mevcut literatür senaryoları (S2 ve S3), genellikle "Sürekli Akış" (Continuous Flow) varsayımıyla çalışmaktadır. Bu durum, modelin 1 tonluk bir atık için bile bir gemi rotası açmasına (mikro sevkiyat) veya acil işlenmesi gereken bir atığı 5 gün süren ucuz bir deniz rotasına yönlendirmesine neden olabilmektedir. Bu çalışma, bu "teorik optimizasyon" ile "gerçek dünya lojistiği" arasındaki boşluğu doldurmayı hedeflemektedir.

## 🎯 Amaç
* Karayolu ve Denizyolu (St. Lawrence Nehri) taşımacılığını entegre ederek:
* Toplam lojistik maliyetleri minimize etmek.
* Sera gazı (GHG) emisyonlarını azaltmak.
* Operasyonel kısıtlar (zaman, kapasite, minimum yük) altında çalışabilir bir ağ kurmak.

## 🚀 Temel Özellikler ve Senaryo 4 Katkısı
Bu repo, literatürdeki standart Doğrusal Programlama (LP) modellerini, gerçek dünya kısıtlarını içeren Karma Tamsayılı Programlama (MIP) modeline dönüştürmüştür.
<img width="600" height="250" alt="Ekran görüntüsü 2026-01-12 194654" src="https://github.com/user-attachments/assets/5b1af3ea-53d3-42e9-8695-c78a1d0cd29e" />

## 🛠️ Kurulum ve Çalıştırma
Bu projeyi yerel makinenizde çalıştırmak için aşağıdaki adımları izleyin.
**Gereksinimler**
* Python 3.x
* PuLP
* Pandas
* Numpy

## 🧠 Sonuçlar ve Karşılaştırma     
**Sadece Senaryo 1- 2 ve 3’ün kodunun çalıştırılması ve sonuçlar**
<img width="515" height="341" alt="image" src="https://github.com/user-attachments/assets/cac6d58f-b00e-44a7-a0a9-7d4d977d4dac" />

Senaryo 1, en yüksek değerlere sahiptir. Sadece kamyon kullanımı, trafik kazası riski, gürültü ve yüksek karbon emisyonu yaratır. Bu senaryo "kirli" ve genellikle "pahalı"dır.
Senaryo 2, finansal anlamda en düşük seviyeye sahiptir. Bu senaryo, uzun mesafeler (Kuzey-Güney hattı) için daha ucuz olan gemileri tercih etmiştir. Şirketler için en karlı senaryodur. 
Hem cepten çıkan para azalır hem de emisyon (kırmızı kısım) S1'e göre düşer.
Senaryo 3, çevreyi korumak için finansal maliyeti artırmayı göze almıştır. 
Örneğin, kamyonla daha ucuza gidecek bir yükü, daha temiz olduğu için gemiye bindirmiş (liman elleçleme maliyetine katlanmış) olabilir.

**Tüm Senaryoların kodunun çalıştırılması ve sonuçlar**

<img width="542" height="418" alt="image" src="https://github.com/user-attachments/assets/4f269d86-17e7-4fae-a820-ce78597e5f44" />

<img width="478" height="395" alt="image" src="https://github.com/user-attachments/assets/8d60d081-f5fa-447b-9e56-b0f0ff6f9a43" />

<img width="507" height="322" alt="image" src="https://github.com/user-attachments/assets/c0cb3af9-1623-4552-b8e2-484bf48a6234" />

<img width="498" height="328" alt="image" src="https://github.com/user-attachments/assets/beb11e55-94d2-4db3-9651-b1d209a6bf87" />

## 🔑 Temel Bulgular 
Analiz edilen dört senaryo arasında S4 (Realistic), 2669 tCO2 toplam emisyon değeri ile en çevreci performansı sergilemiştir. 
Sürdürülebilirlik odaklı S3 senaryosunun (3022 tCO2) dahi altına inilmesi, gerçekçi kısıtların (kapasite sınırları) algoritmayı daha yaratıcı ve verimli rota kombinasyonlarına zorladığını kanıtlamaktadır. 
S4, S1 senaryosuna kıyasla %28 oranında emisyon tasarrufu sağlamaktadır ki bu, gelecekteki potansiyel karbon vergisi maliyetlerini minimize eden stratejik bir kazanımdır.
Lojistik ağların kırılganlığı, darboğaz noktalarındaki yoğunlaşma ile ölçülür. Isı haritası (heatmap) verileri incelendiğinde:
S1 ve S2 senaryolarında yükün Sort_Blue_2 tesisine (%100) ve Sort_Blue_2 tesisine yığıldığı, diğer tesislerin atıl kaldığı görülmektedir. Bu durum, tek bir noktada oluşacak arızanın tüm operasyonu durdurabileceği "Single Point of Failure" (Tek Nokta Hatası) riskini doğurur.
S4 Senaryosu, yükü Sort_CRD_2(%40) ve diğer tesislere daha homojen dağıtarak operasyonel dayanıklılığı (resilience) artırmıştır. 
Tesis kullanımındaki bu denge, operasyonel süreklilik için kritik öneme sahiptir.
S3 senaryosu, emisyonu düşürmek adına teorik olarak 47.000 tonluk bir denizyolu hacmi öngörmüştür. 
Ancak mevcut gemi kapasiteleri ve sefer sıklıkları göz önüne alındığında bu hacim operasyonel riskler taşımaktadır. 
S4 Senaryosu, 10.000 ton seviyesindeki denizyolu kullanımı ile "uygulanabilir" bir intermodal yapı sunmaktadır. 
S4, denizyoluna aşırı bağımlı kalmadan (S3'teki riskten kaçınarak) karayolu rotalarını optimize ederek en düşük emisyonu yakalamayı başarmıştır.
S4 Senaryosunun 5.9 Milyon $ ile en yüksek finansal maliyete sahip olduğu bir gerçektir. Ancak aradaki 1.2 Milyon $'lık fark (S1'e kıyasla), bir "kayıp" değil, bazı risklerin bertaraf edilmesi için ödenen bir prim olarak değerlendirilmelidir.
Bu bağlamda, Senaryo 4 (Realistic), sadece çevresel bir tercih değil, aynı zamanda tedarik zinciri güvenliğini ve sürdürülebilirliğini garanti altına alan en rasyonel stratejik yönetim kararıdır.


