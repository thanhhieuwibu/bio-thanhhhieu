<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Thành Hiếu - Bio Links Siêu Cấp</title>
    <style>
        /* Các biến màu có thể thay đổi động bằng JS */
        :root {
            --bg-start: #ffafbd;
            --bg-end: #ffc3a0;
            --card-bg: rgba(255, 255, 255, 0.7);
            --text-color: #4a4a4a;
            --btn-bg: rgba(255, 255, 255, 0.9);
            --btn-hover-bg: #ff66b2;
            --btn-hover-text: #ffffff;
            --footer-color: rgba(0, 0, 0, 0.4);
        }

        body {
            margin: 0;
            padding: 20px 0;
            box-sizing: border-box;
            background: linear-gradient(135deg, var(--bg-start) 0%, var(--bg-end) 100%);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            position: relative;
            transition: background 0.3s;
        }

        /* Hiệu ứng trái tim bay */
        .bg-hearts {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: 1;
            pointer-events: none;
        }

        .heart-particle {
            position: absolute;
            color: rgba(255, 102, 178, 0.4);
            font-size: 20px;
            animation: floatUp 5s linear infinite;
            bottom: -50px;
        }

        @keyframes floatUp {
            0% { transform: translateY(0) scale(0); opacity: 0; }
            20% { opacity: 0.8; }
            90% { opacity: 0.4; }
            100% { transform: translateY(-110vh) translateX(var(--x-move)) rotate(var(--rot)); opacity: 0; }
        }

        /* Khung Bio chính */
        .bio-container {
            width: 90%;
            max-width: 450px;
            background: var(--card-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 2px solid rgba(255, 255, 255, 0.5);
            padding: 35px 20px;
            border-radius: 30px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            z-index: 2;
            animation: fadeIn 0.8s ease-out;
            position: relative;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Khu vực Avatar */
        .avatar-container {
            position: relative;
            width: 110px;
            height: 110px;
            margin: 0 auto 20px;
            cursor: pointer;
        }

        .avatar {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background-color: #fff;
            border: 4px solid #fff;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 55px;
            overflow: hidden;
            object-fit: cover;
        }

        .verified-badge {
            position: absolute;
            bottom: 5px;
            right: 5px;
            background: #00bfff;
            color: white;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            font-size: 14px;
            display: flex;
            justify-content: center;
            align-items: center;
            border: 2px solid #fff;
        }

        .profile-name {
            font-size: 24px;
            font-weight: bold;
            color: var(--text-color);
            margin: 0 0 8px 0;
        }

        .profile-bio {
            font-size: 14px;
            color: var(--text-color);
            opacity: 0.9;
            margin: 0 0 25px 0;
            line-height: 1.4;
            white-space: pre-line;
        }

        /* Các nút MXH */
        .links-group {
            display: flex;
            flex-direction: column;
            gap: 14px;
            margin-bottom: 25px;
        }

        .bio-link {
            background: var(--btn-bg);
            color: var(--text-color);
            text-decoration: none;
            padding: 14px 20px;
            border-radius: 16px;
            font-size: 16px;
            font-weight: 600;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border: 1px solid rgba(255, 255, 255, 0.5);
            transition: all 0.2s ease;
        }

        .bio-link:hover {
            transform: translateY(-3px);
            background: var(--btn-hover-bg);
            color: var(--btn-hover-text);
            box-shadow: 0 6px 15px rgba(0,0,0,0.1);
        }

        .link-icon-text { display: flex; align-items: center; gap: 12px; }
        .icon { font-size: 20px; }

        /* KHU VỰC ALBUM ẢNH & VIDEO */
        .media-section {
            margin-top: 25px;
            border-top: 1px dashed rgba(0,0,0,0.1);
            padding-top: 20px;
        }

        .media-title {
            font-size: 16px;
            font-weight: bold;
            color: var(--text-color);
            margin-bottom: 15px;
        }

        .gallery {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            margin-bottom: 15px;
        }

        .gallery-img {
            width: 100%;
            height: 120px;
            object-fit: cover;
            border-radius: 12px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.05);
            border: 2px solid #fff;
        }

        .video-container {
            position: relative;
            width: 100%;
            padding-bottom: 56.25%; /* Tỷ lệ 16:9 */
            height: 0;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 8px rgba(0,0,0,0.05);
            border: 2px solid #fff;
        }

        .video-container iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        .footer { 
            margin-top: 30px; 
            font-size: 13px; 
            color: var(--footer-color); 
            font-weight: bold;
            letter-spacing: 0.5px; 
        }

        /* GIAO DIỆN ADMIN CHỈNH SỬA TOÀN DIỆN */
        .admin-modal {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #ffffff;
            border-radius: 30px;
            z-index: 10;
            display: none;
            flex-direction: column;
            padding: 20px;
            box-sizing: border-box;
            overflow-y: auto; /* Cho phép cuộn khi form dài */
        }

        .admin-modal h3 { margin: 0 0 15px 0; color: #ff66b2; text-align: center;}
        
        .form-row {
            display: flex;
            gap: 10px;
            margin-bottom: 10px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            text-align: left;
            margin-bottom: 10px;
            flex: 1;
        }

        .form-group label { font-size: 12px; font-weight: bold; color: #666; margin-bottom: 4px; }
        .form-group input, .form-group textarea {
            padding: 8px 12px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-family: inherit;
            font-size: 13px;
            outline: none;
        }
        .form-group input[type="color"] {
            padding: 2px;
            height: 35px;
            cursor: pointer;
        }
        .form-group input:focus, .form-group textarea:focus { border-color: #ff66b2; }

        .admin-btns { display: flex; gap: 10px; margin-top: 15px; padding-bottom: 20px; }
        .btn { flex: 1; padding: 12px; border: none; border-radius: 10px; font-weight: bold; cursor: pointer; font-size: 14px; }
        .btn-save { background: #4caf50; color: white; }
        .btn-cancel { background: #9e9e9e; color: white; }
    </style>
</head>
<body>

    <div class="bg-hearts" id="heartsContainer"></div>

    <div class="bio-container">
        
        <div class="admin-modal" id="adminModal">
            <h3>🛠️ Hệ Thống Quản Trị Bio</h3>
            
            <div class="form-row">
                <div class="form-group">
                    <label>Tên Hiển Thị</label>
                    <input type="text" id="editName" value="Thành Hiếu">
                </div>
                <div class="form-group">
                    <label>Chữ Ký Footer (YuseiRei...)</label>
                    <input type="text" id="editFooter" value="YuseiRei ♡ wPia">
                </div>
            </div>

            <div class="form-group">
                <label>Lời Giới Thiệu (Bio)</label>
                <textarea id="editBio" rows="2">Welcome to my world! ✨</textarea>
            </div>

            <div class="form-group">
                <label>Link Ảnh Avatar (Hoặc nhập 1 Emoji ví dụ: 🐺)</label>
                <input type="text" id="editAvatar" value="🐺">
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>Link Facebook</label>
                    <input type="text" id="editFb" value="https://www.facebook.com/thahh.hiu">
                </div>
                <div class="form-group">
                    <label>Link TikTok</label>
                    <input type="text" id="editTiktok" value="https://www.tiktok.com/@thanhhieu_2304?is_from_webapp=1&sender_device=pc">
                </div>
            </div>

            <div class="form-row">
                <div class="form-group">
                    <label>Link Ảnh Kỷ Niệm 1</label>
                    <input type="text" id="editImg1" value="https://picsum.photos/300/200?random=1">
                </div>
                <div class="form-group">
                    <label>Link Ảnh Kỷ Niệm 2</label>
                    <input type="text" id="editImg2" value="https://picsum.photos/300/200?random=2">
                </div>
            </div>
            <div class="form-group">
                <label>Mã ID Video YouTube (Ví dụ với clip bài hát: dQw4w9WgXcQ)</label>
                <input type="text" id="editYoutubeId" value="dQw4w9WgXcQ">
            </div>

            <h4 style="margin: 10px 0 5px 0; color: #555; text-align: left;">🎨 Chỉnh Sửa Màu Sắc</h4>
            <div class="form-row">
                <div class="form-group">
                    <label>Màu Nền 1</label>
                    <input type="color" id="colorBgStart" value="#ffafbd">
                </div>
                <div class="form-group">
                    <label>Màu Nền 2</label>
                    <input type="color" id="colorBgEnd" value="#ffc3a0">
                </div>
                <div class="form-group">
                    <label>Màu Chữ</label>
                    <input type="color" id="colorText" value="#4a4a4a">
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>Nền Nút Bấm</label>
                    <input type="color" id="colorBtnBg" value="#ffffff">
                </div>
                <div class="form-group">
                    <label>Nút khi Di Chuột</label>
                    <input type="color" id="colorBtnHover" value="#ff66b2">
                </div>
            </div>

            <div class="admin-btns">
                <button class="btn btn-save" onclick="saveAllData()">LƯU TẤT CẢ</button>
                <button class="btn btn-cancel" onclick="closeAdminPanel()">HỦY BỎ</button>
            </div>
        </div>

        <div class="avatar-container" onclick="openAdminCheck()" title="Click để đăng nhập quản trị">
            <div id="avatarBox" class="avatar">🐺</div>
            <div class="verified-badge">✓</div>
        </div>

        <h2 class="profile-name" id="txt-name">Thành Hiếu</h2>
        <p class="profile-bio" id="txt-bio">Welcome to my world! ✨</p>

        <div class="links-group">
            <a href="https://www.facebook.com/thahh.hiu" target="_blank" class="bio-link" id="link-fb">
                <div class="link-icon-text"><span class="icon">💙</span><span>Facebook cá nhân</span></div>
                <span class="arrow">➔</span>
            </a>
            <a href="https://www.tiktok.com/@thanhhieu_2304?is_from_webapp=1&sender_device=pc" target="_blank" class="bio-link" id="link-tiktok">
                <div class="link-icon-text"><span class="icon">🖤</span><span>Kênh TikTok</span></div>
                <span class="arrow">➔</span>
            </a>
        </div>

        <div class="media-section">
            <div class="media-title">💞 KHOẢNH KHẮC KỶ NIỆM 💞</div>
            <div class="gallery">
                <img id="img-slot-1" src="https://picsum.photos/300/200?random=1" class="gallery-img" alt="Kỷ niệm 1">
                <img id="img-slot-2" src="https://picsum.photos/300/200?random=2" class="gallery-img" alt="Kỷ niệm 2">
            </div>
            <div class="video-container">
                <iframe id="youtube-slot" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
            </div>
        </div>

        <div class="footer" id="txt-footer">YuseiRei ♡ wPia</div>
    </div>

    <script>
        // Tài khoản bảo mật của bạn
        const ADMIN_USER = "thahhiuudeptrai";
        const ADMIN_PASS = "thanhhieu2304";

        const adminModal = document.getElementById('adminModal');

        function openAdminCheck() {
            const userInp = prompt("👤 Tài khoản Admin:");
            if (userInp === null) return;
            const passInp = prompt("🔑 Mật khẩu Admin:");
            if (passInp === null) return;

            if (userInp === ADMIN_USER && passInp === ADMIN_PASS) {
                adminModal.style.display = "flex";
            } else {
                alert("❌ Thông tin đăng nhập không chính xác!");
            }
        }

        function closeAdminPanel() { adminModal.style.display = "none"; }

        // Xử lý lưu dữ liệu và thay đổi giao diện động
        function saveAllData() {
            // 1. Cập nhật chữ và link liên kết
            document.getElementById('txt-name').textContent = document.getElementById('editName').value;
            document.getElementById('txt-bio').textContent = document.getElementById('editBio').value;
            document.getElementById('txt-footer').textContent = document.getElementById('editFooter').value;
            document.getElementById('link-fb').href = document.getElementById('editFb').value;
            document.getElementById('link-tiktok').href = document.getElementById('editTiktok').value;

            // 2. Cập nhật Avatar (Nếu nhập link ảnh thì chuyển sang thẻ img, nếu nhập emoji thì giữ nguyên)
            const avatarVal = document.getElementById('editAvatar').value;
            const avatarBox = document.getElementById('avatarBox');
            if (avatarVal.startsWith('http://') || avatarVal.startsWith('https://')) {
                avatarBox.innerHTML = `<img src="${avatarVal}" style="width:100%; height:100%; object-fit:cover;">`;
            } else {
                avatarBox.textContent = avatarVal || "🐺";
            }

            // 3. Cập nhật Ảnh và Video
            document.getElementById('img-slot-1').src = document.getElementById('editImg1').value;
            document.getElementById('img-slot-2').src = document.getElementById('editImg2').value;
            const ytId = document.getElementById('editYoutubeId').value;
            document.getElementById('youtube-slot').src = `https://www.youtube.com/embed/${ytId}`;

            // 4. Cập nhật Biến màu CSS sắc thái toàn trang
            const root = document.documentElement;
            root.style.setProperty('--bg-start', document.getElementById('colorBgStart').value);
            root.style.setProperty('--bg-end', document.getElementById('colorBgEnd').value);
            root.style.setProperty('--text-color', document.getElementById('colorText').value);
            root.style.setProperty('--btn-bg', document.getElementById('colorBtnBg').value);
            root.style.setProperty('--btn-hover-bg', document.getElementById('colorBtnHover').value);

            alert("✨ Toàn bộ giao diện Bio đã được làm mới thành công!");
            closeAdminPanel();
        }

        // Hiệu ứng hạt trái tim bay lơ lửng ở nền
        const container = document.getElementById('heartsContainer');
        const heartEmojis = ['❤️', '💖', '💕', '💘', '🌸'];
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart-particle');
            heart.textContent = heartEmojis[Math.floor(Math.random() * heartEmojis.length)];
            heart.style.left = Math.random() * 100 + 'vw';
            const size = Math.random() * 15 + 15;
            heart.style.fontSize = size + 'px';
            heart.style.setProperty('--x-move', (Math.random() * 200 - 100) + 'px');
            heart.style.setProperty('--rot', (Math.random() * 360) + 'deg');
            const duration = Math.random() * 3 + 4;
            heart.style.animationDuration = duration + 's';
            container.appendChild(heart);
            setTimeout(() => { heart.remove(); }, duration * 1000);
        }
        setInterval(createHeart, 400);
    </script>
</body>
</html>
