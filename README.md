# REMEMBER TO START ORACLE SERVICE ON EACH MACHINE

## Máy B


```
sqlplus sys as sysdba
Oracle123456
```

```
create user dhqg identified by dhqg;
grant connect, dba to dhqg;
create user sv identified by sv;
grant connect, dba to sv;
create user dhcntt identified by dhcntt;
grant connect, dba to dhcntt;
```

```
connect dhcntt/dhcntt;
```

#### Create data just for testing database link, not important

```
set autocommit on;

CREATE TABLE Khoa (MaKhoa VARCHAR2(50) PRIMARY KEY,MaTruong VARCHAR2(50));

CREATE TABLE Sinhvien (Masv VARCHAR2(8) PRIMARY KEY,Hoten VARCHAR2(50));

```

```
INSERT INTO Khoa (MaKhoa, MaTruong) VALUES ('HTTT_CNTT', 'CNTT');
INSERT INTO Khoa (MaKhoa, MaTruong) VALUES ('KHMT_CNTT', 'CNTT');
INSERT INTO Khoa (MaKhoa, MaTruong) VALUES ('KTMT_CNTT', 'CNTT');
INSERT INTO Khoa (MaKhoa, MaTruong) VALUES ('MMT_CNTT', 'CNTT');
INSERT INTO Khoa (MaKhoa, MaTruong) VALUES ('CNPM_CNTT', 'CNTT');
INSERT INTO Khoa (MaKhoa, MaTruong) VALUES ('KHKT_CNTT', 'CNTT');

INSERT INTO Sinhvien (Masv, Hoten) VALUES ('SV001', 'John Doe');
INSERT INTO Sinhvien (Masv, Hoten) VALUES ('SV002', 'Jane Smith');
INSERT INTO Sinhvien (Masv, Hoten) VALUES ('SV003', 'David Johnson');
INSERT INTO Sinhvien (Masv, Hoten) VALUES ('SV004', 'Emily Davis');
INSERT INTO Sinhvien (Masv, Hoten) VALUES ('SV005', 'Michael Wilson');

```

Open new `cmd`

```
start notepad C:\app\Ora\product\11.2.0\dbhome_1\NETWORK\ADMIN\listener.ora
```

```
start notepad C:\app\Ora\product\11.2.0\dbhome_1\NETWORK\ADMIN\sqlnet.ora
```


## Máy A

Open `cmd` 

```
sqlplus sys as sysdba
Oracle123456
```

```
create user dhqg identified by dhqg;
grant connect, dba to dhqg;
```

```
connect dhqg/dhqg;
```

Open new `cmd`

```
start notepad C:\app\Ora\product\11.2.0\dbhome_1\NETWORK\ADMIN\listener.ora
```

```
start notepad C:\app\Ora\product\11.2.0\dbhome_1\NETWORK\ADMIN\tnsnames.ora
```

```
start notepad C:\app\Ora\product\11.2.0\dbhome_1\NETWORK\ADMIN\sqlnet.ora
```
## Edit hosts file in both mayA and B

Open `cmd` 
```
start notepad C:\WINDOWS\system32\drivers\etc\hosts
```

Add these lines below the line `127.0.0.1 localhost`, replace ip_of_may by the ip address of each machine

```
ip_of_mayB mayB
ip_of_mayA mayA
```

## Command for testing after finish the configuration
```
create public database link dhcntt connect to dhqg identified by dhqg using 'dhcntt';
```
```
select * from dhcntt.sinhvien@dhcntt;
```

## Note

Each machine must have different **MAC address** and **computer name**
Network setting of each machine should be `Host only` or `Bridged` 
