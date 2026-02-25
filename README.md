🤖 ChatbotAI – Self-Hosted LLaMA 3 Chat System

ChatbotAI là hệ thống chatbot AI chạy hoàn toàn local sử dụng mô hình LLaMA 3 thông qua Ollama, kết hợp với FastAPI để cung cấp REST API và giao diện web.

Hệ thống phù hợp cho:

Triển khai nội bộ doanh nghiệp

Phát triển AI cá nhân

Xây dựng nền tảng AI riêng

Môi trường không sử dụng cloud

📌 Tính năng

Chạy mô hình LLaMA 3 local

Không phụ thuộc OpenAI hoặc cloud

REST API dễ tích hợp

Giao diện web đơn giản

Chạy ngầm bằng Windows Service (NSSM)

Có thể mở rộng thêm RAG / memory / auth

🏗 Kiến trúc hệ thống

User (Browser)
↓
FastAPI (app.py)
↓
Ollama API (localhost:11434)
↓
LLaMA 3 Model (8B)

⚙ Yêu cầu hệ thống

Khuyến nghị:

Windows Server 2016+ hoặc Windows 10+

RAM: tối thiểu 16GB

CPU: 4 cores trở lên

Python 3.10+

Ollama đã cài đặt

Không cần GPU (nhưng có GPU sẽ nhanh hơn).

🚀 Cài đặt
1. Cài Ollama

Tải tại:

https://ollama.com

Sau khi cài xong:

ollama run llama3:8b

Kiểm tra model:

ollama list
2. Cài Python

Tải Python 3.10+ (64-bit) từ:

https://www.python.org/downloads/

Sau đó cài thư viện:

python -m pip install --upgrade pip
python -m pip install fastapi uvicorn requests
📁 Cấu trúc dự án
ChatbotAI/
│
├── app.py
├── index.html
└── README.md
▶ Chạy ở chế độ Development

Từ thư mục chứa app.py:

uvicorn app:app --host 0.0.0.0 --port 8000

Truy cập:

http://localhost:8000/docs
🌐 API Endpoint
POST /chat
Request
{
  "message": "Xin chào"
}
Response
{
  "reply": "Chào bạn!"
}
🖥 Chạy ngầm bằng Windows Service (NSSM)
1. Cài NSSM

Tải tại:

https://nssm.cc/download

Giải nén, ví dụ:

C:\nssm
2. Tạo service

Chạy CMD với quyền Administrator:

nssm install ChatbotAI

Cấu hình:

Path:
(đường dẫn tới python.exe)

Ví dụ:

C:\Users\Administrator\AppData\Local\Programs\Python\Python311\python.exe

Startup directory:
(thư mục chứa app.py)

Ví dụ:

E:\ChatbotAI

Arguments:

-m uvicorn app:app --host 0.0.0.0 --port 8000
3. Start service
nssm start ChatbotAI

Cho tự khởi động khi bật máy:

sc config ChatbotAI start= auto
🔍 Kiểm tra trạng thái service
nssm status ChatbotAI

Hoặc mở:

services.msc
⚡ Tối ưu hiệu năng

Với máy 16GB RAM:

Nên dùng: llama3:8b

Hoặc bản quantized

Không nên chạy model 70B

Tránh chạy nhiều ứng dụng nặng cùng lúc

🔮 Hướng phát triển tương lai

Thêm lưu lịch sử chat

Thêm hệ thống đăng nhập

Tích hợp RAG (đọc tài liệu nội bộ)

Thêm streaming response

Triển khai HTTPS

Docker hóa hệ thống

Triển khai Linux (systemd)

📄 License

MIT License

👨‍💻 Tác giả

ChatbotAI – Self Hosted AI System