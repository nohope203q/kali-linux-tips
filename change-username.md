# 🐧 Kali Linux System Configuration Tips

## 1. Đổi Username (Tên người dùng)

> [!CAUTION]
> Không thể thực hiện lệnh này khi đang đăng nhập vào chính user đó. Hãy chuyển sang user **root** hoặc một user khác trước khi làm.

### Các bước thực hiện:

1. **Đổi tên user và di chuyển thư mục Home:**
```bash
sudo usermod -l NEW_USER -d /home/NEW_USER -m OLD_USER
```
* `-l`: Tên mới.
* `-d`: Đường dẫn thư mục home mới.
* `-m`: Di chuyển toàn bộ dữ liệu từ thư mục cũ sang mới.

2. **Đổi tên Group (Nhóm):**
```bash
sudo groupmod -n NEW_USER OLD_USER
```

3. **Cập nhật quyền sở hữu (Nếu cần):**
```bash
sudo chown -R NEW_USER:NEW_USER /home/NEW_USER

```

---

## 2. Đổi Hostname (Tên máy tính)

### Cách 1: Dùng lệnh nhanh (Khuyên dùng)

```bash
sudo hostnamectl set-hostname YOUR_NEW_HOSTNAME

```

### Cách 2: Sửa thủ công (Để đảm bảo ổn định)

1. **Sửa file hostname:**
```bash
sudo nano /etc/hostname

```

*(Xóa tên cũ, ghi tên mới vào rồi lưu lại)*
2. **Sửa file hosts (Quan trọng nhất):**
```bash
sudo nano /etc/hosts

```

Tìm dòng: `127.0.1.1  old_hostname`
Sửa thành: `127.0.1.1  YOUR_NEW_HOSTNAME`
3. **Reboot máy:**
```bash
sudo reboot

```

---

## 3. Lệnh kiểm tra nhanh

| Mục tiêu | Lệnh |
| --- | --- |
| Kiểm tra User hiện tại | `whoami` |
| Xem ID và Group | `id` |
| Kiểm tra Hostname | `hostnamectl` hoặc `hostname` |

---

*Cập nhật lần cuối: 2026*
