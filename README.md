# Website MC Xuân Trang

Trang giới thiệu một trang (single page), không cần cài đặt gì. Chỉ cần đẩy lên GitHub là chạy.

## Cấu trúc thư mục

```
mc-xuan-trang/
├── index.html      ← toàn bộ nội dung, CSS, JavaScript
├── README.md       ← file hướng dẫn này
└── images/         ← ảnh (đã tách từ file PDF profile)
```

---

## 1. Đưa website lên GitHub

1. Đăng nhập https://github.com và bấm **New repository**.
2. Đặt tên, ví dụ `mc-xuan-trang`. Chọn **Public**. Bấm **Create repository**.
3. Tải toàn bộ thư mục `site` về máy, rồi upload lên repo:
   - Trên trang repo, bấm **Add file → Upload files**.
   - Kéo thả `index.html`, `README.md` và thư mục `images/`.
   - Bấm **Commit changes**.
4. Bật GitHub Pages:
   - Vào **Settings → Pages**.
   - Mục **Build and deployment**, chọn **Source: Deploy from a branch**.
   - Chọn nhánh **main**, thư mục **/ (root)**, bấm **Save**.
5. Sau vài phút, website sẽ có địa chỉ dạng:
   `https://<tên-github-của-bạn>.github.io/mc-xuan-trang/`

Mỗi lần sửa file và commit, website tự cập nhật sau 1–2 phút.

---

## 2. Thêm video dẫn của MC Xuân Trang (Google Drive)

Thư mục Drive không nhúng trực tiếp được vào web. Cần lấy **từng file video** và đưa ID vào website.

### Bước 1: Lấy ID của từng video
1. Mở thư mục Drive: https://drive.google.com/drive/folders/1qojTgZIcQEnXpcQoPOip3X1bQW_JfBJQ?usp=drive_link
2. Chuột phải vào một video → **Chia sẻ → Thay đổi thành “Bất kỳ ai có liên kết”** (quan trọng, nếu không khách sẽ không xem được).
3. Bấm **Sao chép liên kết**. Link có dạng:
   `https://drive.google.com/file/d/ABC123xyz456/view?usp=sharing`
4. Phần giữa `/file/d/` và `/view` là **ID**: `ABC123xyz456`.

### Bước 2: Dán ID vào `index.html`
Tìm mảng `VIDEOS` trong phần `<script>` ở cuối file:

```js
const VIDEOS = [
  { title: "Video dẫn #1 – Lễ cưới song ngữ", desc: "Phong cách dẫn Việt – Nhật – Anh", id: "ABC123xyz456" },
  { title: "Video dẫn #2 – Tiệc cưới sang trọng", desc: "Dẫn nghi thức & gameshow", id: "" },
  ...
];
```

- Điền ID vào trường `id`.
- Để trống `id: ""` thì ô video hiện “đang được cập nhật”.
- Muốn thêm video, copy một dòng và đổi thông tin.

### Lưu ý
- Video phải để **“Bất kỳ ai có liên kết”** mới phát được trên web.
- Có thể đổi tên tiêu đề và mô tả ở `title` và `desc` tùy ý.

---

## 3. Cài đặt Viber

Trong `index.html`, tìm `+84XXXXXXXXX` (có 3 chỗ: nút Viber nổi, nút “Nhắn qua Viber”, và trong phần liên hệ). Thay bằng số Viber thật, ví dụ:

```
viber://chat?number=%2B84901234567
```

Lưu ý:
- Bỏ số 0 đầu, thêm `+84`, rồi mã hoá dấu `+` thành `%2B`.
- Nút **Viber nổi** nằm góc phải dưới, luôn hiển thị khi cuộn trang.
- Số điện thoại trong nút “Gọi điện” cũng đổi tương tự: `tel:+84901234567`.

---

## 4. Chỉnh sửa nội dung nhanh

| Muốn đổi | Tìm trong `index.html` |
|---|---|
| Tên, slogan | `<h1 id="heroTitle">` và `class="tagline"` |
| Đoạn giới thiệu | Mục `id="about"` |
| Số năm, số lễ cưới | `data-count="6"` và `data-count="400"` |
| Thêm ảnh sự kiện | Copy một `<figure>` trong `.gallery`, đổi `src` và `alt` |
| Màu chủ đạo | Biến `--gold` trong `:root` |
| Dịch vụ | Mục `id="services"` |

**Thêm ảnh mới:** bỏ ảnh vào thư mục `images/`, rồi viết:
```html
<figure><img src="images/ten-anh.jpg" alt="Mô tả ảnh" loading="lazy"></figure>
```

---

## 5. Hiệu ứng chuyển động đã có

- Ảnh nền hero chuyển động chậm (zoom nhẹ).
- Tiêu đề hiện từng chữ.
- Nội dung và ảnh hiện dần khi cuộn tới.
- Số liệu đếm lên khi hiện ra.
- Ảnh phóng to khi bấm (lightbox), đóng bằng phím Esc.
- Nút Viber nhấp nháy nhẹ để thu hút chú ý.
- Tự tắt chuyển động nếu máy người dùng bật chế độ giảm chuyển động.

---

## 6. Lưu ý trước khi công bố

- Các số `XXXXXXXXX` và link fanpage (`facebook.com/`) cần thay bằng thông tin thật.
- Kiểm tra quyền riêng tư của ảnh và video: chỉ đưa lên những hình đã được cặp đôi đồng ý.
- Ảnh trong thư mục `images/` được tách từ file PDF profile. Nên dùng ảnh gốc chất lượng cao nếu có.
