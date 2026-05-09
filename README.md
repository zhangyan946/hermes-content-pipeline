# Hermes Content Pipeline

> **Hermes Agent 驱动的多模态内容自动生成管线**
>
> 从信息采集 → 语义分解 → AI 生图 → 内容编排 → 质量校验，全链路自动化。

## 📌 项目简介

基于 Hermes Agent 调度中枢，集成火山引擎即梦AI 4.6 图像生成模型、浏览器自动化采集、文件系统渲染，实现**旅游文化导览页面的全自动生成**。目前已落地兵马俑、塔尔寺等多个景点的导览网页产出。

### 解决的核心痛点

| 痛点 | 解决方案 |
|------|----------|
| **图文「文不对图」** — 网络图片经常防盗链失效、内容张冠李戴 | 文本语义驱动 AI 定向生图，每张插图精准对应章节内容 |
| **内容生产效率瓶颈** — 人工制作需数小时 | 全链路压缩到分钟级，产出质量稳定可控 |
| **多工具碎片化** — 浏览器/API/渲染各自独立 | Hermes Agent 统一调度，跨工具上下文传递 |

## 🏗️ 架构设计

### 五阶段长链推理管线

```
外部数据源 → [Stage 1 信息采集] → [Stage 2 语义分解] → [Stage 3 图像生成] → [Stage 4 内容编排] → [Stage 5 质量校验] → 产出
                                                    ↑                              |
                                                    └──── QA FAIL 回溯生图 ────────┘
```

1. **信息采集层** — Browser Automation Agent 访问百科等来源，结构化提取文本
2. **语义分解层** — Hermes 调度中枢拆解章节，生成精准图像提示词
3. **图像生成层** — 即梦AI 4.6 逐章节定向生图，确保语义一致性
4. **内容编排层** — HTML/CSS/JS 渲染引擎，暗色博物馆主题，响应式布局
5. **质量校验层** — 逐章交叉验证图文对应，发现不匹配自动回溯修正

> 📊 完整架构图：[hermes-agent-workflow.html](./hermes-agent-workflow.html)

### 多 Agent 协作

- **Hermes 中枢 Agent** — 任务分解与调度
- **Browser Agent** — 信息抓取与结构化
- **Image Agent** (即梦AI 4.6) — 视觉内容生成
- **File System Agent** — 渲染与持久化
- **QA Agent** — 质量校验闭环

## 🎯 在线演示

| 景点 | 演示链接 |
|------|----------|
| 🏛️ 秦始皇兵马俑 | [兵马俑导览.html](./兵马俑导览.html) |
| 🛕 塔尔寺 | [塔尔寺导览.html](./塔尔寺导览.html) |

> 所有页面为**单文件静态 HTML**，内嵌完整 CSS/JS，可直接在浏览器中离线打开。

## 🛠️ 技术栈

- **调度中枢**: Hermes Agent
- **图像生成**: 火山引擎 即梦AI 4.6 (图片生成模型)
- **信息采集**: Browser Automation
- **内容渲染**: 原生 HTML5 + CSS3 + 暗色博物馆主题
- **质量保障**: 自动交叉验证 + 回溯修正

## 📂 项目结构

```
hermes-content-pipeline/
├── README.md                     # 项目说明
├── hermes-agent-workflow.html    # 架构图
├── 兵马俑导览.html                # 兵马俑导览页
├── 塔尔寺导览.html                # 塔尔寺导览页
└── images/
    ├── bmy/                      # 兵马俑插图
    │   ├── pit1.jpg
    │   ├── kneeling-archer.jpg
    │   ├── cavalry.jpg
    │   ├── general-figure.jpg
    │   ├── bronze-chariot.jpg
    │   ├── bronze-sword.jpg
    │   └── color-restoration.jpg
    └── ters/                     # 塔尔寺插图
        ├── ters_panorama.jpg
        ├── ters_dajinwa.jpg
        ├── ters_babao_stupas.jpg
        └── ters_suyouhua.jpg
```

---

**张焱软件** · 2026
