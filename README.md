# 🚀 GitHub Actions Self-Hosted Runner (Dockerized)

Repo này cung cấp image Docker để triển khai **GitHub Actions self-hosted runner** trên nhiều môi trường:  
✅ Linux  
✅ macOS  
✅ Windows

Hỗ trợ:

- Repo-level runner
- Org-level runner
- Multi-replica (scale nhiều runner cùng lúc)
- Auto remove runner khi container stop
- Config dễ dàng qua environment variables

---

## ⚙️ 1. Chuẩn bị

1. Vào repository hoặc organization mà bạn muốn gắn runner:

   - Repo: `Settings → Actions → Runners → New self-hosted runner`
   - Org: `Organization settings → Actions → Runners → New self-hosted runner`

2. Tạo **Personal Access Token (PAT)** loại **classic** (không phải fine-grained) tại:  
   [Settings → Developer settings → Personal access tokens → Tokens (classic)]

   Chọn scope:

   - `repo` (nếu private repo, còn public repo thì `public_repo` là đủ)
   - `workflow`
   - `admin:repo_hook`

---

## 🛠️ 2. Environment Variables

| Tên biến         | Bắt buộc | Mô tả                                                                   |
| ---------------- | -------- | ----------------------------------------------------------------------- |
| `REPO`           | ✅       | Repository theo dạng `owner/repo` (VD: `thienbui176/ExpenseManagement`) |
| `TOKEN`          | ✅       | PAT (classic) có scope hợp lệ                                           |
---

## 🐳 3. Chạy bằng Docker

### Repo-level runner (một repo cụ thể)

```bash
docker run -d \
  -e REPO="thienbui176/ExpenseManagement" \
  -e TOKEN="ghp_xxx..." \
  --name my-runner \
  runner-image:latest
```

```bash 
REPO=xxx PAT=yyy docker-compose up -d 
```