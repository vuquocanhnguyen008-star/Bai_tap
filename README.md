[README.md](https://github.com/user-attachments/files/33421534/README.md)
# Bài 3 - Pipeline PowerShell
1. Giới thiệu

Bài tập này thuộc nội dung thực hành về Pipeline trong PowerShell. Qua bài tập, em tìm hiểu cách sử dụng Pipeline để kết hợp các lệnh với nhau nhằm xử lý dữ liệu trong file log.

Bài toán yêu cầu tìm các dòng chứa từ TIMEOUT, loại bỏ các dòng chứa NOT TIMEOUT và đếm số dòng còn lại. Ngoài ra, em thực hiện so sánh cách giải bằng PowerShell và Git Bash để hiểu sự khác nhau giữa hai môi trường.
 
 2. Phân tích đề bài

Bài này yêu cầu sử dụng Pipeline để lọc các dòng trong file log có chứa từ TIMEOUT, nhưng không lấy những dòng có NOT TIMEOUT. Sau đó đếm số dòng còn lại.

Em sẽ sử dụng các lệnh có sẵn trong PowerShell và Git Bash để giải quyết bài toán.

Các bước thực hiện:
- Đọc file log.txt.
- Lọc những dòng có chứa TIMEOUT.
- Bỏ những dòng có NOT TIMEOUT.
- Đếm số dòng còn lại.

 3. Cách giải

# 3.1. Sử dụng PowerShell

powershell
@(Get-Content ".\log.txt" | Select-String "TIMEOUT" | Where-Object { $_.Line -notmatch "NOT TIMEOUT" }).Count


Giải thích:

- Get-Content: Đọc file log.
- Select-String "TIMEOUT": Lọc các dòng có chữ TIMEOUT.
- Where-Object: Loại bỏ những dòng có NOT TIMEOUT.
- @(...): Gom kết quả lại để đếm.
- .Count: Đếm số dòng còn lại.

# 3.2. Sử dụng Git Bash

bash
grep "TIMEOUT" log.txt | grep -v "NOT TIMEOUT" | wc -l


Giải thích:

- grep "TIMEOUT" log.txt: Tìm dòng có TIMEOUT.
- grep -v "NOT TIMEOUT": Bỏ các dòng có NOT TIMEOUT.
- wc -l: Đếm số dòng còn lại.

 4. So sánh PowerShell và Git Bash

| PowerShell | Git Bash |
|---|---|
| Dùng Get-Content để đọc file | Dùng grep để tìm nội dung |
| Dùng Where-Object để lọc dữ liệu | Dùng grep -v để loại bỏ dòng |
| Dùng .Count để đếm kết quả | Dùng wc -l để đếm dòng |
| Pipeline truyền các đối tượng | Pipeline chủ yếu truyền văn bản |
| Phù hợp với Windows | Có các lệnh quen thuộc của Linux/Unix |

Theo em, cả hai cách đều giải quyết được yêu cầu của bài. PowerShell có nhiều lệnh riêng để xử lý dữ liệu, còn Git Bash viết ngắn gọn hơn khi làm việc với văn bản.
