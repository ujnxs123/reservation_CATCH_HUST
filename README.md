# reservation_CATCH_HUST
Committed to building a script for grabbing appointments from HUST and an easy-to-interact GUI interface.
# HUST预约系统定时抢票工具 🎯

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-开发中-yellow.svg)]()

一个专为华中科技大学预约系统设计的自动化抢票工具，支持定时预约、多账号管理、智能重试等功能。

## ✨ 功能特性

- 🕐 **定时预约**: 支持精确到秒的定时预约功能
- 👥 **多账号管理**: 支持多个账号同时抢票，提高成功率
- 🔄 **智能重试**: 网络异常或服务器繁忙时自动重试
- 📱 **实时通知**: 支持微信、邮件等多种通知方式
- 🎯 **精准抢票**: 支持指定场次、座位等精确预约
- 📊 **日志记录**: 详细的操作日志，便于问题排查
- 🛡️ **安全防护**: 模拟真实用户行为，避免被系统检测

## 🚀 快速开始

### 环境要求

- Python 3.8+
- Chrome浏览器
- 稳定的网络连接

### 安装依赖

```bash
# 克隆项目
git clone https://github.com/yourusername/reservation_CATCH_HUST.git
cd reservation_CATCH_HUST

# 安装依赖
pip install -r requirements.txt

# 安装Chrome驱动（自动下载）
python setup_driver.py
```

### 配置文件

复制配置模板并填写您的信息：

```bash
cp config/config.example.json config/config.json
```

编辑 `config/config.json`：

```json
{
  "accounts": [
    {
      "username": "your_student_id",
      "password": "your_password",
      "name": "账号1"
    }
  ],
  "reservation": {
    "target_time": "2024-01-15 12:00:00",
    "venue": "体育馆",
    "activity": "羽毛球",
    "duration": "2小时"
  },
  "notification": {
    "enable": true,
    "methods": ["email", "wechat"],
    "email": "your_email@example.com"
  },
  "advanced": {
    "retry_times": 5,
    "retry_interval": 1,
    "headless": true
  }
}
```

### 运行程序

```bash
# 立即运行
python main.py

# 定时运行（推荐在预约开放前几分钟启动）
python main.py --schedule "2024-01-15 11:59:50"
```

## 📁 项目结构

```
reservation_CATCH_HUST/
├── README.md                 # 项目说明文档
├── requirements.txt          # Python依赖包
├── main.py                  # 主程序入口
├── setup_driver.py          # 驱动安装脚本
├── config/
│   ├── config.json          # 用户配置文件
│   └── config.example.json  # 配置文件模板
├── src/
│   ├── __init__.py
│   ├── reservation.py       # 预约核心逻辑
│   ├── scheduler.py         # 定时任务管理
│   ├── notification.py      # 通知功能
│   ├── account_manager.py   # 账号管理
│   └── utils/
│       ├── __init__.py
│       ├── logger.py        # 日志工具
│       ├── browser.py       # 浏览器控制
│       └── helpers.py       # 辅助函数
├── logs/                    # 日志文件目录
├── drivers/                 # 浏览器驱动目录
└── tests/                   # 测试文件
    ├── __init__.py
    └── test_reservation.py
```

## 🔧 高级配置

### 多账号配置

```json
{
  "accounts": [
    {
      "username": "student_id_1",
      "password": "password_1",
      "name": "主账号",
      "priority": 1
    },
    {
      "username": "student_id_2", 
      "password": "password_2",
      "name": "备用账号",
      "priority": 2
    }
  ]
}
```

### 通知配置

支持多种通知方式：

- **邮件通知**: 配置SMTP服务器信息
- **微信通知**: 通过Server酱或企业微信
- **钉钉通知**: 通过钉钉机器人
- **Telegram**: 通过Telegram Bot

### 定时策略

```json
{
  "schedule": {
    "mode": "precise",           // 精确模式
    "target_time": "12:00:00",   // 目标时间
    "advance_seconds": 10,       // 提前启动秒数
    "max_wait_time": 300         // 最大等待时间
  }
}
```

## 📝 使用说明

### 1. 准备工作

- 确保您的学号和密码正确
- 提前了解预约系统的开放时间
- 测试网络连接稳定性

### 2. 运行建议

- 建议在预约开放前2-3分钟启动程序
- 使用多个账号提高成功率
- 选择网络稳定的环境运行

### 3. 常见问题

**Q: 程序运行后没有反应？**
A: 检查配置文件是否正确，查看logs目录下的日志文件

**Q: 提示登录失败？**
A: 确认学号密码正确，检查是否需要验证码

**Q: 抢票失败？**
A: 可能是网络延迟或服务器繁忙，建议调整重试参数

## 🤝 贡献指南

欢迎提交Issue和Pull Request！

1. Fork本项目
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建Pull Request

## ⚠️ 免责声明

- 本工具仅供学习交流使用
- 请遵守学校相关规定，合理使用预约系统
- 使用本工具产生的任何后果由用户自行承担
- 建议适度使用，避免对服务器造成过大压力

## 📄 许可证

本项目采用 [MIT License](LICENSE) 许可证。

## 🙏 致谢

- 感谢华中科技大学提供的预约系统
- 感谢所有贡献者的支持和建议
- 感谢开源社区提供的优秀工具和库

---

**⭐ 如果这个项目对您有帮助，请给个Star支持一下！**

## 📞 联系方式

- 项目地址: [GitHub Repository](https://github.com/yourusername/reservation_CATCH_HUST)
- 问题反馈: [Issues](https://github.com/yourusername/reservation_CATCH_HUST/issues)
- 邮箱: your_email@example.com

---

*最后更新: 2024年1月*
