# Laporan Mingguan Job 6 – Seven Segment

**Nama** : Cut Qatrunada Nasywa Mahadewi  
**NPM** : 2410017514008  
**Program Studi** : TRKJ  
**Mata Kuliah** : LAB IV Basic Analog Electronic  

---

## Tujuan Praktikum

Tujuan dari praktikum ini adalah untuk:

- Mengetahui prinsip kerja display seven segment  
- Memahami perbedaan seven segment common cathode dan common anode  
- Mampu menghubungkan seven segment dengan Arduino Uno  
- Menampilkan angka 0–9 menggunakan pemrograman Arduino  

---

## Teori

Seven Segment Display (SSD) adalah komponen elektronika yang terdiri dari tujuh buah LED (segmen) yang disusun membentuk angka **8**. Setiap segmen diberi label **a, b, c, d, e, f, dan g**. Dengan menyalakan kombinasi segmen tertentu, seven segment dapat menampilkan angka 0–9.

### Jenis Seven Segment
- **Common Cathode (CC)**  
  Semua kaki katoda disatukan dan dihubungkan ke **GND**. Segmen menyala jika pin Arduino diberi logika **HIGH**.
- **Common Anode (CA)**  
  Semua kaki anoda disatukan dan dihubungkan ke **VCC (+5V)**. Segmen menyala jika pin Arduino diberi logika **LOW**.

---

## Kombinasi Segmen Angka

| Angka | Segmen Menyala |
|------|----------------|
| 0 | a, b, c, d, e, f |
| 1 | b, c |
| 2 | a, b, d, e, g |
| 3 | a, b, c, d, g |
| 4 | b, c, f, g |
| 5 | a, c, d, f, g |
| 6 | a, c, d, e, f, g |
| 7 | a, b, c |
| 8 | a, b, c, d, e, f, g |
| 9 | a, b, c, d, f, g |

---

## Peralatan

- Laptop  
- Arduino Uno  
- Breadboard  
- Seven Segment Display (1 digit – Common Cathode)  
- Resistor 220Ω – 330Ω (7 buah)  
- Kabel jumper  
- Kabel USB  

---

## Rangkaian Praktikum

Rangkaian menggunakan seven segment **Common Cathode**. Setiap segmen dihubungkan ke pin digital Arduino melalui resistor pembatas arus.

### Koneksi Pin

| Segmen | Pin Arduino |
|------|-------------|
| a | 2 |
| b | 3 |
| c | 4 |
| d | 5 |
| e | 6 |
| f | 7 |
| g | 8 |
| COM | GND |

---

## Prosedur Praktikum

1. Siapkan Arduino Uno, seven segment, resistor, dan breadboard  
2. Hubungkan setiap segmen ke pin Arduino melalui resistor  
3. Hubungkan kaki COM ke GND Arduino  
4. Buka Arduino IDE  
5. Masukkan source code seven segment  
6. Upload program ke board Arduino  
7. Amati tampilan angka 0–9 pada seven segment  

---

## Dokumentasi
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/a818368a-de6f-4a29-a1c0-f6a85dc59a29" />

## source code
int a = 2;
int b = 3;
int c = 4;
int d = 5;
int e = 6;
int f = 7;
int g = 8;

void setup() {
  pinMode(a, OUTPUT);
  pinMode(b, OUTPUT);
  pinMode(c, OUTPUT);
  pinMode(d, OUTPUT);
  pinMode(e, OUTPUT);
  pinMode(f, OUTPUT);
  pinMode(g, OUTPUT);
}

void loop() {
  for (int i = 0; i <= 9; i++) {
    tampil(i);
    delay(1000);
  }
}

void tampil(int angka) {
  digitalWrite(a, LOW);
  digitalWrite(b, LOW);
  digitalWrite(c, LOW);
  digitalWrite(d, LOW);
  digitalWrite(e, LOW);
  digitalWrite(f, LOW);
  digitalWrite(g, LOW);

  switch (angka) {
    case 0: digitalWrite(a,HIGH); digitalWrite(b,HIGH); digitalWrite(c,HIGH);
            digitalWrite(d,HIGH); digitalWrite(e,HIGH); digitalWrite(f,HIGH); break;
    case 1: digitalWrite(b,HIGH); digitalWrite(c,HIGH); break;
    case 2: digitalWrite(a,HIGH); digitalWrite(b,HIGH); digitalWrite(d,HIGH);
            digitalWrite(e,HIGH); digitalWrite(g,HIGH); break;
    case 3: digitalWrite(a,HIGH); digitalWrite(b,HIGH); digitalWrite(c,HIGH);
            digitalWrite(d,HIGH); digitalWrite(g,HIGH); break;
    case 4: digitalWrite(b,HIGH); digitalWrite(c,HIGH);
            digitalWrite(f,HIGH); digitalWrite(g,HIGH); break;
    case 5: digitalWrite(a,HIGH); digitalWrite(c,HIGH); digitalWrite(d,HIGH);
            digitalWrite(f,HIGH); digitalWrite(g,HIGH); break;
    case 6: digitalWrite(a,HIGH); digitalWrite(c,HIGH); digitalWrite(d,HIGH);
            digitalWrite(e,HIGH); digitalWrite(f,HIGH); digitalWrite(g,HIGH); break;
    case 7: digitalWrite(a,HIGH); digitalWrite(b,HIGH); digitalWrite(c,HIGH); break;
    case 8: digitalWrite(a,HIGH); digitalWrite(b,HIGH); digitalWrite(c,HIGH);
            digitalWrite(d,HIGH); digitalWrite(e,HIGH); digitalWrite(f,HIGH); digitalWrite(g,HIGH); break;
    case 9: digitalWrite(a,HIGH); digitalWrite(b,HIGH); digitalWrite(c,HIGH);
            digitalWrite(d,HIGH); digitalWrite(f,HIGH); digitalWrite(g,HIGH); break;
  }
}
