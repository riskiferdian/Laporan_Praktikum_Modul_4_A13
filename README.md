# Laporan_Praktikum_Modul_4_A13

## Kelompok A13
### 05111840000011 – Bryan Gautama Ngo 
### 05111840000052 – Riski Anang Ferdian

## 1.	VLSM (Menggunakan CPT)

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/1.jpg)
 
-	Menentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan melakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan.

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/2.png)

Berdasarkan total IP dan netmask yang dibutuhkan, maka kita dapat menggunakan netmask /19 untuk memberikan pengalamatan IP pada subnet.

-	Membuat pohon untuk perhitungan dan pembagian IP

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/3.jpg)

- Melakukan Routing pada router

a. SURABAYA

 - MALANG
 - A2
 - A4
 - A5
 - A7
 - A8
 - A9
 - A10
 - A11
 - A12
 - A13
 
b. PROBOLINGGO

 - DEFAULT
 
c. PASURUAN

 - DEFAULT
 - A4
 - A8
 
d. BATU

 - DEFAULT
 - MALANG
 - A9
 - A12
 - A13
 
e. MADIUN

 - DEFAULT
 
f. KEDIRI

 - DEFAULT
 - A12
 
g. BLITAR

 - DEFAULT

## 2.	CIDR (Menggunakan UML)

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/4.jpg)

-	Subnet B1 merupakan hasil penggabungan dari subnet A12 dan subnet A13
-	Subnet B2 merupakan hasil penggabungan dari subnet A4 dan subnet A8
-	Subnet B3 merupakan hasil penggabungan dari subnet A5 dan subnet A9
-	Subnet C1 merupakan hasil penggabungan dari subnet B1 dan subnet A11
-	Subnet C2 merupakan hasil penggabungan dari subnet B2 dan subnet A3
-	Subnet C3 merupakan hasil penggabungan dari subnet B3 dan subnet A10
-	Subnet D1 merupakan hasil penggabungan dari subnet C1 dan subnet C3
-	Subnet D2 merupakan hasil penggabungan dari subnet C2 dan subnet A7
-	Subnet E1 merupakan hasil penggabungan dari subnet D1 dan subnet A6
-	Subnet E2 merupakan hasil penggabungan dari subnet D2 dan subnet A2
-	Subnet F1 merupakan hasil penggabungan dari subnet E1 dan subnet A1
-	Subnet G1 merupakan hasil penggabungan dari subnet F1 dan subnet E2
 
-	Pembagian IP dengan pohon berdasarkan penggabungan subnet yang telah dilakukan

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/5.jpg)

## Topologi

```
# Switch
uml_switch -unix switch0 > /dev/null < /dev/null &
uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch2 > /dev/null < /dev/null &
uml_switch -unix switch3 > /dev/null < /dev/null &
uml_switch -unix switch4 > /dev/null < /dev/null &
uml_switch -unix switch5 > /dev/null < /dev/null &
uml_switch -unix switch6 > /dev/null < /dev/null &
uml_switch -unix switch7 > /dev/null < /dev/null &
uml_switch -unix switch8 > /dev/null < /dev/null &
uml_switch -unix switch9 > /dev/null < /dev/null &
uml_switch -unix switch10 > /dev/null < /dev/null &
uml_switch -unix switch11 > /dev/null < /dev/null &
uml_switch -unix switch12 > /dev/null < /dev/null &
uml_switch -unix switch13 > /dev/null < /dev/null &
uml_switch -unix switch14 > /dev/null < /dev/null &

# Router
xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,'10.151.72.57' eth1=daemon,,,switch1 eth2=daemon,,,switch2 eth3=daemon,,,switch7 eth4=daemon,,,switch0 mem=64M &
xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch2 eth1=daemon,,,switch3 eth2=daemon,,,switch8 mem=64M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch3 eth1=daemon,,,switch4 eth2=daemon,,,switch9 mem=64M &
xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch7 eth1=daemon,,,switch11 eth2=daemon,,,switch10 eth3=daemon,,,switch6 mem=64M &
xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch6 eth1=daemon,,,switch5 mem=64M &
xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch11 eth1=daemon,,,switch14 eth2=daemon,,,switch12 mem=64M &
xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch14 eth1=daemon,,,switch13 mem=64M &

# Server
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch0 mem=64M &
xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch12 mem=64M &

# Klien
xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch1 mem=64M &
xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch4 mem=64M &
xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch9 mem=64M &
xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch9 mem=64M &
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch8 mem=64M &
xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch14 mem=64M &
xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch13 mem=64M &
xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch10 mem=64M &
xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch5 mem=64M &
xterm -T JOMBANG -e linux ubd0=JOMBANG,jarkom umid=JOMBANG eth0=daemon,,,switch6 mem=64M &
```

## Pengaturan UML

a. Uncomment ipv4 forward untuk setiap router

b. Penambahan setting network interface untuk setiap UML 

- SURABAYA

```
auto eth0
iface eth0 inet static
address 10.151.72.58
netmask 255.255.255.252
gateway 10.151.72.57

#A1/22
auto eth1
iface eth1 inet static
address 192.168.64.1
netmask 255.255.252.0

#A2/30
auto eth2
iface eth2 inet static
address 192.168.192.1
netmask 255.255.255.252

#A6/30
auto eth3
iface eth3 inet static
address 192.168.32.1
netmask 255.255.255.252

auto eth4
iface eth4 inet static
address 10.151.73.113
netmask 255.255.255.252
```

- PASURUAN

```
#A2/30
auto eth0
iface eth0 inet static
address 192.168.192.2
netmask 255.255.255.252
gateway 192.168.192.1

#A3/30
auto eth1
iface eth1 inet static
address 192.168.144.1
netmask 255.255.255.252

#A7/22
auto eth2
iface eth2 inet static
address 192.168.160.1
netmask 255.255.252.0
```

- PROBOLINGGO

```
#A3/30
auto eth0
iface eth0 inet static
address 192.168.144.2
netmask 255.255.255.252
gateway 192.168.144.1

#A4/25
auto eth1
iface eth1 inet static
address 192.168.136.1
netmask 255.255.255.128

#A8/21
auto eth2
iface eth2 inet static
address 192.168.128.1
netmask 255.255.248.0
```

- BATU

```
#A6/30
auto eth0
iface eth0 inet static
address 192.168.32.2
netmask 255.255.255.252
gateway 192.168.32.1

#A11/30
auto eth1
iface eth1 inet static
address 192.168.8.1
netmask 255.255.255.252

#A10/22
auto eth2
iface eth2 inet static
address 192.168.20.1
netmask 255.255.252.0

#A5/23
auto eth3
iface eth3 inet static
address 192.168.16.1
netmask 255.255.254.0
```

- MADIUN

```
#A5/23
auto eth0
iface eth0 inet static
address 192.168.16.2
netmask 255.255.254.0
gateway 192.168.16.1

#A9/28
auto eth1
iface eth1 inet static
address 192.168.18.1
netmask 255.255.255.240
```

- KEDIRI

```
#A11/30
auto eth0
iface eth0 inet static
address 192.168.8.2
netmask 255.255.255.252
gateway 192.168.8.1

#A13/24
auto eth1
iface eth1 inet static
address 192.168.4.1
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 10.151.73.117
netmask 255.255.255.252
```

- BLITAR

```
#A13/24
auto eth0
iface eth0 inet static
address 192.168.4.2
netmask 255.255.255.0
gateway 192.168.4.1

#A12/22
auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.252.0
```

- MOJOKERTO

```
auto eth0
iface eth0 inet static
address 10.151.73.114
netmask 255.255.255.252
gateway 10.151.73.113
```

- MALANG

```
auto eth0
iface eth0 inet static
address 10.151.73.118
netmask 255.255.255.252
gateway 10.151.73.117
```

- SAMPANG

```
#A1/22
auto eth0
iface eth0 inet static
address 192.168.64.2
netmask 255.255.252.0
gateway 192.168.64.1
```

- BONDOWOSO

```
#A4/25
auto eth0
iface eth0 inet static
address 192.168.136.2
netmask 255.255.255.128
gateway 192.168.136.1
```

- JEMBER

```
#A8/21
auto eth0
iface eth0 inet static
address 192.168.128.2
netmask 255.255.248.0
gateway 192.168.128.1
```

- BANYUWANGI

```
#A8/21
auto eth0
iface eth0 inet static
address 192.168.128.3
netmask 255.255.248.0
gateway 192.168.128.1
```

- SIDOARJO

```
#A7/22
auto eth0
iface eth0 inet static
address 192.168.160.2
netmask 255.255.252.0
gateway 192.168.160.1
```

- LUMAJANG

```
#A13/24
auto eth0
iface eth0 inet static
address 192.168.4.3
netmask 255.255.255.0
gateway 192.168.4.1
```

- TULUNGAGUNG

```
#A12/22
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.252.0
gateway 192.168.0.1
```

- NGANJUK

```
#A10/22
auto eth0
iface eth0 inet static
address 192.168.20.2
netmask 255.255.252.0
gateway 192.168.20.1
```

- BOJONEGORO

```
#A9/28
auto eth0
iface eth0 inet static
address 192.168.18.2
netmask 255.255.255.240
gateway 192.168.18.1
```

- JOMBANG

```
#A5/23
auto eth0
iface eth0 inet static
address 192.168.16.3
netmask 255.255.254.0
gateway 192.168.16.1
```

## Routing

Kita tidak perlu menambahkan default routing pada router di UML karena sudah ada. Sehingga kita hanya menambahkan routing pada router SURABAYA, PASURUAN, BATU, DAN KEDIRI

- SURABAYA, routing dilakukan untuk D1, D2, dan MALANG

```
route add -net 192.168.0.0 netmask 255.255.224.0 gw 192.168.32.2
route add -net 192.168.128.0 netmask 255.255.192.0 gw 192.168.192.2
route add -net 10.151.73.116 netmask 255.255.255.252 gw 192.168.32.2
```

- PASURUAN, routing dilakukan untuk B2

```
route add -net 192.168.128.0 netmask 255.255.240.0 gw 192.168.144.2
```

- BATU, routing dilakukan untuk B1, A9, dan MALANG

```
route add -net 192.168.0.0 netmask 255.255.248.0 gw 192.168.8.2
route add -net 192.168.18.0 netmask 255.255.255.240 gw 192.168.16.2
route add -net 10.151.73.116 netmask 255.255.255.252 gw 192.168.8.2
```

- KEDIRI, routing dilakukan untuk A12

```
route add -net 192.168.0.0 netmask 255.255.252.0 gw 192.168.4.2
```

## Testing UML

untuk testing disini kami melakukan ping ke its.ac.id

- SURABAYA

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/6.png)

- PASURUAN

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/7.png)

- PROBOLINGGO

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/8.png)

- KEDIRI

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/9.png)

- BATU

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/10.png)

- BLITAR

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/11.png)

- MADIUN

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/12.png)

- SAMPANG

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/13.png)

- BONDOWOSO

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/14.png)

- BANYUWANGI

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/15.png)

- JEMBER

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/16.png)

- SIDOARJO

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/17.png)

- MOJOKERTO

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/18.png)

- JOMBANG

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/19.png)

- LUMAJANG

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/20.png)

- BOJONEGORO

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/21.png)

- NGANJUK

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/22.png)

- MALANG

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/23.png)

- TULUNGAGUNG

![Gambar](https://github.com/riskiferdian/Laporan_Praktikum_Modul_4_A13/blob/main/images/24.png)
