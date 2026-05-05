# VitaCare AI: Hệ thống Hỏi đáp Y tế Tiếng Việt (RAG-based)

![LLM](https://img.shields.io/badge/Llama--3.1--8B-Fine--tuned-orange) ![RAG](https://img.shields.io/badge/Architecture-RAG-green)


## 📌 Giới thiệu dự án
Dự án xây dựng một hệ thống hỏi đáp trong lĩnh vực y tế dành cho người Việt. Bằng cách kết hợp sức mạnh của các Mô hình ngôn ngữ lớn (LLM) và kiến trúc **Retrieval-Augmented Generation (RAG)**, hệ thống có khả năng cung cấp các câu trả lời chính xác, đáng tin cậy và có dẫn chứng từ nguồn tri thức y khoa uy tín.

## ✨ Tính năng nổi bật
*   **Kiến trúc RAG:** Giảm thiểu hiện tượng "ảo giác" (hallucination) của LLM bằng cách truy xuất thông tin từ cơ sở dữ liệu tri thức ngoài trước khi sinh câu trả lời.
*   **Fine-tuned Llama 3.1 8B:** Mô hình được tinh chỉnh chuyên biệt cho văn phong và kiến thức y tế tiếng Việt bằng kỹ thuật LoRA.
*   **Cơ sở tri thức rộng lớn:** Hơn 168,000 đoạn văn bản y tế được trích xuất và vector hóa từ nguồn dữ liệu uy tín (Vinmec).
*   **Giao diện thân thiện:** Ứng dụng web được xây dựng bằng Streamlit, hỗ trợ quản lý lịch sử hội thoại và hiển thị nguồn tham khảo.

## 🏗️ Kiến trúc hệ thống
Hệ thống bao gồm 3 thành phần chính:
1.  **Module Truy xuất (Retriever):** Sử dụng mô hình `paraphrase-multilingual-mpnet-base-v2` để nhúng câu hỏi và tìm kiếm ngữ cảnh tương đồng trong **Qdrant Vector Database**.
2.  **Module Sinh câu trả lời (Generator):** Sử dụng mô hình `Llama-3.1-8B-Instruct` đã được fine-tune để tổng hợp thông tin từ ngữ cảnh và sinh câu trả lời tự nhiên.
3.  **Module Điều phối:** Sử dụng framework **LangChain** để kết nối các thành phần và quản lý luồng dữ liệu.

## 🛠️ Công nghệ sử dụng
*   **Mô hình ngôn ngữ:** Llama 3.1 8B (Meta AI)
*   **Thư viện Fine-tuning:** Unsloth, LoRA/QLoRA
*   **Framework LLM:** LangChain
*   **Cơ sở dữ liệu Vector:** Qdrant
*   **Embedding Model:** paraphrase-multilingual-mpnet-base-v2 (Sentence-Transformers)
*   **Giao diện:** Streamlit

## 📂 Cấu trúc mã nguồn
*   `Tạo_dữ_liệu_để_finetune.ipynb`: Quy trình xử lý dữ liệu thô, nhúng vector và xây dựng Knowledge Base trên Qdrant.
*   `finetunellama-3-1-8b-20-05.ipynb`: Quy trình tinh chỉnh mô hình Llama 3.1 8B bằng Unsloth trên GPU.
*   `metric-bleu.ipynb`: Đánh giá chất lượng câu trả lời của hệ thống bằng chỉ số BLEU so với bộ dữ liệu kiểm thử.
*   `streamlit-11f7c9.ipynb`: Mã nguồn triển khai ứng dụng Web UI cho người dùng cuối.

## 📊 Kết quả thực nghiệm
Mô hình sau khi fine-tune cho thấy sự cải thiện về khả năng hiểu ngữ cảnh y tế chuyên biệt. Chỉ số **BLEU** đạt mức ổn định, câu trả lời sinh ra bám sát ngữ cảnh được cung cấp và có độ chính xác cao hơn so với các mô hình chưa được tinh chỉnh.

---
*Dự án này được thực hiện vì mục đích nghiên cứu học thuật. Luôn tham khảo ý kiến bác sĩ chuyên khoa cho các vấn đề sức khỏe thực tế.*
