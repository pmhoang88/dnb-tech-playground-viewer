# d&b Tech Playground Hà Nội · viewer 3D

## Mục tiêu
Xem model SketchUp của Tech Playground Hà Nội trên điện thoại hoặc máy bất kỳ, không cần mở SketchUp.

## Ràng buộc
- Giao diện: một trang, model 3D phía trên, danh sách layer phía dưới (điện thoại) hoặc bên phải (màn hình rộng). Chữ tiếng Việt.
- Tính năng: gom theo layer (ghế, bàn, đèn, truss, loa, tường, thảm…), không dùng component; truss chỉ giữ phần trong venue (khung tường 20_Ballroom_Walls); giữ màu gốc của vật liệu.
- Code: three.js r128 + GLTFLoader; model là GLB nén gzip, lưu dạng base64 trong model.json; có dự phòng giải nén bằng pako cho iOS cũ; nền 3D cố định màu sáng.
- Dung lượng model.json khoảng 1–2 MB.

## Kế hoạch
| Bước | Trạng thái |
|---|---|
| /ballroom/: file DB_tech_playground (29/10) | xong |
| /ballroom-v2/: file DB_tech_playground mới (29/10) | xong |
| /ballroom-v3/: file DB_Tech_Playground_021126 (02/11) | xong |

## Nhật ký
- 2026-10-29: tạo /ballroom/, gom layer, bỏ truss ngoài venue.
- 2026-10-29: sửa màn hình đen trên iOS cũ (thêm giải nén pako, khai báo UTF-8, bỏ CSS `inset`).
- 2026-10-29: tạo /ballroom-v2/; tăng ánh sáng, cố định nền sáng (model tối màu bị đen thui).
- 2026-11-02: tạo /ballroom-v3/ từ DB_Tech_Playground_021126.skp; thêm layer riêng Rack ampli D90, Tag U5; CabinetsMainArray xếp vào Loa; tăng độ chi tiết (truss gần như đủ mặt).

## Log lỗi
| Thời điểm | Triệu chứng | Nguyên nhân | Cách sửa | Trạng thái |
|---|---|---|---|---|
| 2026-10-29 | iPhone 8 iOS cũ: đen thui | thiếu DecompressionStream, Blob.stream | thêm pako 2.1.0 dự phòng | đã sửa |
| 2026-10-29 | Chữ tiếng Việt lỗi trên GitHub Pages | thiếu `<meta charset="utf-8">` | thêm meta | đã sửa |
| 2026-10-29 | /ballroom-v2/ đen thui | ánh sáng yếu, nền tối ở chế độ tối | tăng đèn, nền sáng cố định | đã sửa |

## Còn thiếu
- Chưa rõ "U5" là thiết bị gì; đang để layer riêng "Tag U5".
- /ballroom/ (bản cũ nhất) chưa áp dụng bản sửa ánh sáng.
- Chưa thử trên iPhone 8 thật.
