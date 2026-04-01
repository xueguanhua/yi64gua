# 易经64卦 Web 应用规范

## 1. Concept & Vision

一个沉浸式的易经64卦探索应用，以中国传统水墨美学为基调，呈现古典智慧的庄重与深邃。用户可按卦序浏览64卦，点击进入详情页查看卦象、卦辞、爻辞及详细解读，体验传统文化的韵味。

## 2. Design Language

### Aesthetic Direction
新中式水墨风格 - 以宣纸质感为背景，墨色为主调，朱红为点缀，呈现古典书籍的质感。

### Color Palette
- Primary (墨色): `#2c2c2c`
- Secondary (朱砂): `#c41e3a`
- Accent (金色): `#b8860b`
- Background (宣纸): `#f5f0e6`
- Text (深墨): `#1a1a1a`
- Muted (淡墨): `#8b8b8b`

### Typography
- 标题: "Noto Serif SC", serif (700 weight)
- 正文: "Noto Serif SC", serif (400 weight)
- 辅助: "LXGW WenKai", serif

### Spatial System
- 基础单位: 8px
- 卡片间距: 24px
- 内容区最大宽度: 1200px
- 详情页宽度: 800px

### Motion Philosophy
- 页面切换: 淡入淡出 (opacity 0→1, 300ms ease-out)
- 卡片悬停: 轻微上浮 + 阴影加深 (transform translateY -4px, 200ms)
- 卦象符号: 缓慢显现 (opacity 0→1, 600ms ease-out)

### Visual Assets
- 卦象使用 Unicode 符号: ☰(乾)、☱(兑)、☲(离)、☳(震)、☴(巽)、☵(坎)、☶(艮)、☷(坤)
- 阳爻: ⚊ (一长横)
- 阴爻: ⚋ (两短横)
- 装饰: 印章风格图标

## 3. Layout & Structure

### 首页 (卦列表)
- 顶部: 应用标题 "易经64卦" + 简短副标题
- 主体: 8×8 网格布局展示64卦
- 每个卦卡: 卦序号 + 卦名 + 卦象符号
- 底部: 简约footer

### 详情页
- 返回按钮 (左上角)
- 卦象大字展示 (居中，卦象符号 + 卦名)
- 卦辞 section
- 六爻 section (展示各爻)
- 爻辞 section (逐爻解释)
- 详细解读 section

### Responsive Strategy
- Desktop (>1024px): 8列网格
- Tablet (768-1024px): 6列网格
- Mobile (<768px): 4列网格

## 4. Features & Interactions

### 核心功能
1. **浏览64卦**: 首页网格展示，按先天序排列
2. **查看详情**: 点击任意卦卡进入详情页
3. **返回导航**: 详情页可返回首页继续浏览

### 交互细节
- 卡片悬停: 显示淡墨色边框 + 轻微上浮
- 卡片点击: 页面淡出后切换到详情页
- 返回按钮: 点击返回首页，页面淡入

### 数据展示
每个卦包含:
- 序号 (1-64)
- 卦名 (中文)
- 英文名
- 卦象 (上下卦组合)
- 卦辞
- 六爻 (从初爻到上爻)
- 爻辞 (6条)
- 详细解读

## 5. Component Inventory

### HexagramCard (卦卡)
- 默认: 米色背景，卦序、卦名、卦象垂直排列
- 悬停: 边框加深，上浮效果
- 点击: 触发页面切换

### DetailHeader (详情页头部)
- 大字卦象符号
- 卦名 + 英文名
- 分隔线 (朱红色)

### SectionBlock (内容区块)
- 标题 (带朱红装饰线)
- 内容文字
- 底部留白

### BackButton (返回按钮)
- 默认: 墨色文字 + 左箭头
- 悬停: 朱红色

## 6. Technical Approach

### 架构
- 纯前端单页应用
- 单 HTML 文件，内嵌 CSS 和 JavaScript
- 使用 CSS Grid 布局
- Vanilla JavaScript 实现页面切换

### 数据
- 64卦数据以内嵌 JSON 数组存储
- 每个卦完整数据: 卦名、卦象、卦辞、六爻、爻辞、解读

### 路由
- 首页: 展示64卦网格
- 详情页: 路由参数 `/hexagram/{id}`
- 使用 hash 路由实现无刷新切换
