﻿# my-vscode-project
AI Auto Publisher 是一个全自动化的内容发布系统，结合 代理管理、账号管理、用户存储、任务队列（Celery） 进行自动化运营，支持多平台的内容发布，并可与 AI 结合生成个性化数字人内容。
🔥 主要功能

自动化内容发布：支持多平台（如 Twitter、Reddit、TikTok、B 站等）的自动文章/视频发布。

账号管理：多账号轮询发布，避免封号和风控。

代理池管理：通过代理池切换 IP，支持自动检测有效代理。

任务调度：基于 Celery + Redis 的任务队列，支持批量任务执行。

AlphaMorph & Shuxing Future （未来规划）：结合 DeepMind SIMA / Habitat 进行 AI 互动和 3D 任务执行。

内容智能优化：集成 OpenAI API，可自动生成文章、短视频字幕等。
🛠 技术栈

Python 3.x

Flask / FastAPI（后台 API）

Selenium / undetected_chromedriver（自动化浏览器）

Celery + Redis（任务队列）

Prometheus + Grafana（系统监控）

PostgreSQL / MongoDB（数据存储）

OpenAI API / DeepMind Habitat（AI 交互）
1️⃣ 克隆项目
 git clone https://github.com/tinninhi/my-vscode-project.git
 cd my-vscode-project
2️⃣ 创建虚拟环境并安装依赖 
 python -m venv venv
 source venv/bin/activate  # Mac/Linux
 venv\Scripts\activate  # Windows
 pip install -r requirements.txt
3️⃣ 配置环境变量
在 项目根目录 创建 .env 文件，添加如下内容：
 API_KEY=your_api_key
 REDIS_URL=redis://localhost:6379
 DATABASE_URL=postgresql://user:password@localhost:5432/dbname
4️⃣ 运行服务
redis-server
启动 Celery 任务队列
celery -A main.celery worker --loglevel=info
运行 Flask API
python main.py
🎯 使用方法

1️⃣ 运行自动发布任务
 curl -X POST http://127.0.0.1:5000/publish -d "text=测试文章"
2️⃣ 监控任务状态
 curl http://127.0.0.1:5000/monitor
📂 代码结构
📂 my-vscode-project
 ├── config.py             # 环境变量和配置信息
 ├── main.py               # 项目主入口，任务调度
 ├── platforms.py          # 平台规则与支持
 ├── account_manager.py    # 账号管理
 ├── proxy_manager.py      # 代理池管理
 ├── enhanced_publisher.py # 内容发布逻辑
 ├── user_storage.py       # 用户存储管理
 ├── monitor.py            # 任务监控
 ├── requirements.txt      # 依赖库
 ├── README.md             # 说明文档
 ❗ 常见问题

1️⃣ 发布失败？

✅ 确保 Selenium + ChromeDriver 版本匹配。
✅ 检查代理 IP 是否有效。
✅ 账户是否被风控（检查 account_manager.py）。

2️⃣ 任务未执行？

✅ 确保 Celery 任务队列已启动。
✅ 检查 Redis 连接状态。

🔮 未来优化方向

集成 AI 自动生成视频内容

优化 AI 数字人，让 AI 可实时互动

支持更多社交平台自动化发布

🤝 贡献指南

欢迎 Pull Request 或 Issue 提交建议！

Fork 本仓库

创建新分支 (git checkout -b feature-branch)

提交更改 (git commit -m "添加新功能")

推送分支 (git push origin feature-branch)

创建 Pull Request

🚀 期待你的贡献！
