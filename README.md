# 口腔溃疡预防健康管理（OralCare Health Manager）

记录每日饮食作息，自动计算健康评分，守护口腔健康。纯前端单文件应用（PWA），数据只保存在你自己的浏览器本地。

## ✨ 功能特性（V1.6.1）

- **每日健康打卡**：12 项饮食/作息评分项 + 午间睡眠时长 + 夜间睡眠时长（4 档计分）+ 一键全选
- **口腔溃疡症状记录**：无 / 轻微 / 中度 / 重度，日历右上角用紫色小火焰直观展示（1~3 个）
- **健康评分趋势图**：周 / 月 / 季 / 年 4 个视图，季视图标注关键日期，80 分目标虚线
- **日历视图**：简洁深色 UI，放大日期数字，有症状记录的日期自动点亮紫色火焰
- **自定义评分**：侧边抽屉可编辑评分项名称和分值分布，改动即时生效
- **数据备份**：一键导出全部记录为 JSON，可跨设备导入恢复
- **PWA 离线可用**：可安装到手机/桌面，断网也能正常使用
- **夜间模式**：深色 UI，长时间使用更护眼

## 🚀 部署到 GitHub Pages（约 3 分钟）

只需推送以下文件即可上线（其余开发文件可不推）：

```
index.html              # 主应用（唯一入口）
manifest.webmanifest    # PWA 清单
sw.js                   # 离线缓存 Service Worker
icon-192.svg            # 应用图标 192
icon-512.svg            # 应用图标 512
README.md
.gitignore
```

### 步骤

1. **创建仓库**：GitHub → New repository → 填仓库名（如 `oral-health`）→ Create
2. **初始化并推送**（在 `C:\Users\ThinkPad\Desktop\1.5` 目录打开命令行）：
   ```bash
   git init
   git add index.html manifest.webmanifest sw.js icon-192.svg icon-512.svg README.md .gitignore
   git commit -m "口腔健康管理 V1.6.1"
   git branch -M main
   git remote add origin https://github.com/你的用户名/oral-health.git
   git push -u origin main
   ```
3. **开启 Pages**：仓库页面 → Settings → Pages → Build and deployment → Source 选 **Deploy from a branch** → Branch 选 `main`、目录选 `/ (root)` → Save
4. 等待 1~2 分钟，访问：`https://你的用户名.github.io/oral-health/`（仓库名替换）

> 以后每次改代码：`git add . && git commit -m "说明" && git push` 即可自动更新。

### 自定义域名（可选）

仓库根目录放一个 `CNAME` 文件，内容写你的域名（如 `health.example.com`），再到域名服务商加一条 CNAME 记录指向 `你的用户名.github.io`。

## 💻 本地运行

- **最简单**：直接双击 `index.html` 用浏览器打开即可使用
- **本地服务器（推荐，体验 PWA）**：
  ```bash
  cd C:\Users\ThinkPad\Desktop\1.5
  python -m http.server 8080
  # 浏览器访问 http://localhost:8080
  ```

## 💾 数据与备份

- 数据保存在浏览器 **localStorage**（键 `oral_care_records_v1`），刷新、关浏览器、重启电脑都不会丢
- **跨设备迁移**：旧设备用「导出备份」生成 JSON → 新设备打开页面点「导入恢复」即可
- ⚠️ 注意：部署到 GitHub Pages 后是新网址，浏览器不会自动带旧数据过来，请用上面的导出/导入迁移
- 清除浏览器站点数据会清空记录，建议定期「导出备份」

## 📁 项目结构

```
1.5/
├── index.html              # 应用本体（全部功能在此）
├── manifest.webmanifest    # PWA 配置
├── sw.js                   # 离线缓存
├── icon-192.svg / icon-512.svg
├── README.md
└── (开发资产：test/ 自动化测试、tools/ 补丁脚本，可不推送)
```

## 📜 版本历史

- **V1.6.1**：季/年视图柱状图修复；抽屉评分编辑生效修复；日历简化（去分数、放大日期、紫色火焰）；评分项文案调整（夜间睡眠时长 / 午间睡眠时长 / 适量饮水6次·日）
- **V1.6**：夜间模式、睡眠 4 档单选组、症状强制校验、一键全选、紫色火焰日历、4 视图图表、导入修复
- **V1.5**：自定义评分基线、评分项编辑、数据导出/导入
- **V1.4-PWA**：PWA 离线支持、数据本地持久化

## 🧪 自动化测试（开发用）

```bash
cd C:\Users\ThinkPad\Desktop\1.5
npm install          # 安装 jsdom（仅测试需要）
node test/run-all.js # 11 个测试全绿
```
