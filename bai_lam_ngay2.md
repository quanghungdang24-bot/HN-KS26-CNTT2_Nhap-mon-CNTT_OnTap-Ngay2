# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên:** Đặng Quang Hưng 
- **Lớp:** CNTT2
- **Link repository:**
- **Hệ điều hành (Windows/macOS):** Windows

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```shell
gc .\logs\access.log | select-string "ERROR" > .\logs\error_report.txt
gc .\logs\error_report.txt
```

### 2 dòng lỗi đầu tiên trong error_report.txt

```text
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)

```

## Bài 2. Đếm bằng pipeline

### Lệnh

```shell
gc .\logs\access.log | select-string "WARNING" | Measure-Object
gc .\logs\payment.log | select-string "ERROR" | Measure-Object

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log: 4
ERROR trong payment.log: 3
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
.\auto_warning.ps1

```

### Nội dung file logs/warning_report.txt

```text
=== CANH BAO THANH TOAN ===

2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi

```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
"=== TONG HOP ACCESS LOG ===" > .\logs\tong_hop_ngay2.tx
gc .\logs\access.log | select-string "ERROR" >> .\logs\tong_hop_ngay2.txt
(gc .\logs\payment.log | select-string "WARNING").Count >> .\logs\tong_hop_ngay2.txt
```

### Nội dung file logs/tong_hop_ngay2.txt

```text
=== TONG HOP ACCESS LOG ===

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)


5

```

## Bài 5. Câu hỏi ngắn

- **a)** Lệnh > sử dụng để xóa/ghi đè tất cả nội dung cũ; Lệnh >> dùng để thêm nội dung vào cuối file , nối tiếp thông tin (không xóa nội dung cũ) 
- **b)** Nếu dùng > thay cho >> thì sẽ mất toàn bộ nội dung trong file, thông tin bị ghi đè, làm mất đi dòng tiêu đề của lệnh 1, chỉ còn lại các dòng ERROR
- **c)** Sử dụng đường dẫn tương đối giúp script có thể chạy trên nhiều máy mà không xảy ra lỗi như đường dẫn tuyệt đối

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** ..../100
- **Lỗi mình đã mắc và cách sửa:**
