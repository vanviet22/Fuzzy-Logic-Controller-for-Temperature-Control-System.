# Fuzzy Logic Controller for Temperature Control System

## Giới thiệu
Đề tài xây dựng bộ điều khiển mờ (Fuzzy Logic Controller - FLC) cho hệ thống điều khiển nhiệt độ và so sánh với bộ điều khiển PID truyền thống.  
Hệ thống mô phỏng việc điều chỉnh tốc độ quạt dựa trên nhiệt độ trong phòng và nhiệt độ ngoài trời nhằm duy trì nhiệt độ phòng ổn định và tiết kiệm năng lượng.

## Mục tiêu
- Tìm hiểu về Logic mờ (Fuzzy Logic)
- Xây dựng hệ suy luận mờ (Fuzzy Inference System)
- Thiết kế bộ điều khiển mờ cho hệ thống nhiệt độ
- Mô phỏng bằng Python với thư viện scikit-fuzzy
- Xây dựng bộ điều khiển PID để so sánh
- Đánh giá hiệu năng giữa FLC và PID

## Công nghệ sử dụng
- Python
- scikit-fuzzy
- NumPy
- Matplotlib

## Thiết kế bộ điều khiển mờ

### Đầu vào
- Nhiệt độ trong phòng (Ti): [0, 50]
- Nhiệt độ ngoài trời (To): [0, 50]

### Đầu ra
- Vận tốc quạt (v): [0, 600 vòng/phút]

### Tập mờ

Nhiệt độ:
- Rất lạnh
- Lạnh
- Vừa
- Nóng
- Rất nóng

Vận tốc quạt:
- Dừng
- Chậm
- Trung bình
- Nhanh
- Tối đa

### Luật mờ

Ví dụ:

- IF Ti là Nóng AND To là Nóng THEN Quạt Nhanh
- IF Ti là Vừa THEN Quạt Trung bình
- IF Ti là Lạnh THEN Quạt Chậm

Tổng số luật: 25 luật

### Các bước suy luận mờ

1. Fuzzification (Làm mờ)
2. Áp dụng toán tử AND / OR
3. Suy diễn luật
4. Tổng hợp kết quả
5. Giải mờ (Centroid)

## Bộ điều khiển PID

PID điều khiển dựa trên sai số:

e(t) = Tset - Ti

Công thức:

u(t) = Kp * e(t) + Ki * integral + Kd * derivative

PID sử dụng mô hình hệ thống để tính nhiệt độ mới theo vận tốc quạt.


Kết quả:
- PID điều khiển chính xác theo nhiệt độ đặt
- FLC điều khiển mượt và tiết kiệm năng lượng hơn
- FLC cần thiết kế luật tốt để tránh làm lạnh quá mức
