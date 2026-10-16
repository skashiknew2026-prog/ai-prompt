<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ভিডিও আপলোড অ্যাডমিন প্যানেল</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        body {
            background-color: #0f172a;
            color: #f8fafc;
            padding: 20px;
        }
        .admin-container {
            max-width: 600px;
            margin: 40px auto;
            background: #1e293b;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
        }
        h2 {
            margin-bottom: 20px;
            color: #38bdf8;
            text-align: center;
        }
        .form-group {
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
        }
        input[type="text"],
        textarea,
        input[type="file"] {
            width: 100%;
            padding: 12px;
            background: #0f172a;
            border: 1px solid #334155;
            border-radius: 6px;
            color: #fff;
            font-size: 14px;
        }
        textarea {
            resize: vertical;
            height: 100px;
        }
        button {
            width: 100%;
            padding: 12px;
            background: #0284c7;
            border: none;
            border-radius: 6px;
            color: white;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.3s;
        }
        button:hover {
            background: #0369a1;
        }
        .preview-box {
            margin-top: 20px;
            text-align: center;
        }
        video {
            max-width: 100%;
            border-radius: 6px;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <div class="admin-container">
        <h2>🎥 ভিডিও আপলোড প্যানেল</h2>
        <form id="uploadForm">
            <div class="form-group">
                <label for="videoTitle">ভিডিওর শিরোনাম (Title):</label>
                <input type="text" id="videoTitle" placeholder="ভিডিওর নাম লিখুন..." required>
            </div>

            <div class="form-group">
                <label for="videoDesc">বর্ণনা (Description):</label>
                <textarea id="videoDesc" placeholder="ভিডিও সম্পর্কে কিছু লিখুন..."></textarea>
            </div>

            <div class="form-group">
                <label for="videoFile">ভিডিও ফাইল নির্বাচন করুন:</label>
                <input type="file" id="videoFile" accept="video/*" required>
            </div>

            <button type="submit">আপলোড করুন</button>
        </form>

        <div class="preview-box" id="previewContainer"></div>
    </div>

    <script>
        const form = document.getElementById('uploadForm');
        const videoFile = document.getElementById('videoFile');
        const previewContainer = document.getElementById('previewContainer');

        form.addEventListener('submit', function(e) {
            e.preventDefault();
            const title = document.getElementById('videoTitle').value;
            const desc = document.getElementById('videoDesc').value;
            const file = videoFile.files[0];

            if (file) {
                const videoURL = URL.createObjectURL(file);
                previewContainer.innerHTML = `
                    <p style="color: #34d399; margin-bottom: 10px;">সফলভাবে আপলোড হয়েছে!</p>
                    <h3>${title}</h3>
                    <p style="font-size: 13px; color: #94a3b8; margin-bottom: 10px;">${desc}</p>
                    <video controls src="${videoURL}"></video>
                `;
                alert('ভিডিও সফলভাবে যুক্ত করা হয়েছে!');
                form.reset();
            }
        });
    </script>

</body>
</html>
