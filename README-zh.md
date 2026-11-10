# 26Flow（中文说明）

**26Flow** 是一个可视化工作流浏览器扩展，用你已登录的 [Muse.ai](https://muse.ai) 会话来创建图片和视频。在画布上连接节点、生成媒体，再把视频片段排到时间线上。

[English](README.md) · [详细中文使用指南](使用指南.md)

**快速安装：** [下载 MuseFlow-extension.zip](https://github.com/bynne2602/museflow/raw/refs/heads/main/downloads/MuseFlow-extension.zip) · 不需要安装 npm，也不需要构建。

## 界面截图

### 演示视频

[![观看 MuseFlow：用 Muse.ai 创建图片、生成视频并组装场景](https://img.youtube.com/vi/w7mJwTJyzKw/maxresdefault.jpg)](https://www.youtube.com/watch?v=w7mJwTJyzKw)

[▶ 在 YouTube 上观看](https://www.youtube.com/watch?v=w7mJwTJyzKw) · [下载演示视频 MP4](https://github.com/bynne2602/museflow/releases/download/demo-2026-10-09/2026-10-09.11-17-18.mp4)

### 视频教程

[![观看 MuseFlow 工作流教程](https://img.youtube.com/vi/_n4B9V-Daro/hqdefault.jpg)](https://www.youtube.com/watch?v=_n4B9V-Daro)

[▶ 在 YouTube 上观看 MuseFlow 教程](https://www.youtube.com/watch?v=_n4B9V-Daro)

### 工作流画布与 Muse.ai

![26Flow 工作流画布已连接 Muse.ai 会话](docs/screenshots/26flow-workflow-canvas.png)

### 时间线预览

![26Flow 在时间线预览面板中播放已生成的场景](docs/screenshots/26flow-timeline-preview.png)

### 时间线编辑器

![26Flow 时间线：片段顺序、缩略图与时长控制](docs/screenshots/26flow-timeline-editor.png)

## 功能

- **可视化节点画布：** 添加、移动、连接、多选和排列工作流节点。按住 **Alt** 拖动可复制节点或选中节点组（含输入连接）；按 **Ctrl+Z** 撤销最近一次画布或工作流编辑。按 **G** 再拖动画布可画出节点分组框；按 **T** 可在画布上直接添加自由文本备注。备注可以拖动、编辑，并随工作流一起保存。分组框也会随工作流保存。支持画布平移缩放，右键菜单可操作节点。
- **提示词工具：** 创建提示词、负面提示词、追加或合并文本；Text Merge（文本合并）可在同一个输入口接受多个文本来源，按连接顺序以自定义分隔符拼接。
- **图片工作流：** 提供图片输入与参考图，生成图片、调整尺寸、预览已连接的媒体。
- **视频工作流：** 生成视频片段，可选用上一个时间线片段的结尾帧作为连续性参考，并预览已连接的视频。
- **时间线：** 添加和排列片段、设置片段时长、预览整个序列，导出 WebM，或用内置的本地 FFmpeg 引擎把整条时间线合成为 MP4（H.264）。MP4 处理全程在你的设备上完成。
- **剧本转节点：** 把按场景写的剧本转成已连接的图片/视频节点和排好序的时间线。在剧本导入器里下载严格填写模板，它规定了必填标题、字段名和场景结构。解析器接受 `Scene 1 (...)` 标题（旧的越南语 `CẢNH 1 (...)` 和中文 `场景 1 (...)` 剧本仍可导入），并展开共用的提示词锁定块。**剧本本身请用英文写：Muse 对英文的视频和音频指示遵循得最可靠。**
- **选择性运行工作流：** 先查看生成顺序、拖动排序，再单独勾选要运行的图片/视频节点。如果被选节点需要某个尚未生成的源输出，MuseFlow 会发出警告。
- **工作流文件：** 用 **Save workflow** 把工作流下载为可重复使用的 JSON 文件，用 **Import workflow** 恢复。已生成和输入的媒体在可能的情况下会内嵌进文件；无法访问的远程媒体仍保留原始链接。
- **本地保存：** **Save** 按钮和自动保存会把当前工作流保存在浏览器扩展存储中。

## 系统要求

- 支持 Manifest V3 扩展的 Chromium 内核浏览器。
- 一个处于登录状态的 Muse.ai 会话。生成媒体时请保持 Muse.ai 聊天页打开。
- Muse.ai 账号与页面功能须支持你请求的生成。画面比例、音频和视频可用性取决于 Muse.ai。

26Flow 通过扩展的页面桥接与 Muse.ai 通信，不使用 muse2api、独立的生成后端、API 密钥、Docker 或 npm 构建步骤。运行生成时，提示词和选中的参考图会提交给 Muse.ai。时间线 MP4 导出使用扩展内置的 FFmpeg WebAssembly 引擎，在本地处理视频。

## 安装

1. 下载 [MuseFlow-extension.zip](https://github.com/bynne2602/museflow/raw/refs/heads/main/downloads/MuseFlow-extension.zip) 并解压到一个固定文件夹。也可以[下载仓库 ZIP](https://github.com/bynne2602/museflow/archive/refs/heads/main.zip)。
2. 打开浏览器的扩展管理页（Chrome 是 `chrome://extensions`）。
3. 打开 **开发者模式（Developer mode）**。
4. 选择 **加载已解压的扩展程序（Load unpacked）**，指向包含 `manifest.json` 的文件夹。
5. 打开 Muse.ai，登录并进入聊天页。
6. 打开 **26Flow**，检查 Muse 会话状态。

不需要安装 npm，也不需要构建步骤。下载的 ZIP 包含扩展源码和内置的本地 FFmpeg 文件。使用 **Load unpacked** 时，请选择解压后直接包含 `manifest.json` 的那个文件夹。

### 下载打包好的 ZIP

打包好的 ZIP 包含扩展、内置 FFmpeg 文件和必需的许可声明。请先解压，再用 **Load unpacked** 选择包含 `manifest.json` 的文件夹，不要直接选 ZIP 文件本身。

### 更新

从 0.5.1 版开始，MuseFlow 在打开应用时会自动检查新版本。如有新版，状态栏会出现一条小通知并附带 ZIP 下载链接；你可以忽略通知，也可以随时自行下载更新。替换文件后，在浏览器扩展管理页点 **Reload（重新加载）**，再重新加载 Muse.ai 标签页。

低于 0.5.1 的旧版没有更新检查器，需要手动安装一次 0.5.1，之后才能收到后续版本的通知。

## 把 MuseFlow 和 Muse.ai 并排显示

为了在工作时看得更清楚，可以同时显示 Muse.ai 聊天和 MuseFlow 画布：

1. 在一个浏览器窗口中打开 Muse.ai 聊天。
2. 点击 MuseFlow 扩展图标，在新标签页中打开画布。把该标签页拖出标签栏，拆成独立窗口。
3. Windows 系统：选中 MuseFlow 窗口，按 **Windows 键 + 左方向键**；选中 Muse.ai 窗口，按 **Windows 键 + 右方向键**。也可以把两个窗口分别拖到屏幕左边缘和右边缘。
4. 生成期间保持两个页面都打开，这样既能看到 MuseFlow 里正在运行的节点，也能看到 Muse.ai 里的生成回复。

## 快速上手

1. 添加一个 **Prompt** 节点，输入提示词。
2. 添加一个 **Generate Image**（生成图片）或 **Generate Video**（生成视频）节点。
3. 把 Prompt 节点的输出拖到生成节点的提示词输入口，再连接需要的参考图或其他输入。
4. 选择输出参数，点击节点上的 **Run Image** 或 **Run Video**，或从工具栏运行整个工作流。
5. 把生成结果连到 **Preview** 节点查看。视频则加入 **Timeline**（时间线），排好顺序后预览或导出。

用剧本建工作流时，选择 **Script → Nodes**，下载严格模板，自己填写或把模板连同故事梗概交给 AI 填写。标题和字段顺序不要改动。MuseFlow 识别 `Scene 1 (0:00–0:05): Title`（以及旧的 `CẢNH 1 (...)` / `场景 1 (...)` 标题）、开场/结尾画面、按秒编排的动作、开场图提示词、视频提示词和音频指示。提示词和 Audio（音频）字段请用英文写。共用提示词锁定块会展开进各场景的提示词。每个场景会生成已连接的图片/视频节点；视频按场景顺序排上时间线，后续场景开启连续性。

## 数据与权限

工作流和本地保存的媒体保存在你设备上的浏览器扩展存储中。运行工作流时，26Flow 会通过你已登录的会话，把相关提示词和参考媒体提交给 Muse.ai。扩展请求浏览器存储和标签页访问权限，用于保存工作流和与 Muse.ai 通信；它不设独立的 26Flow 账号，也不设独立的生成服务器。

## 故障排查

- **Muse 会话不可用：** 登录 Muse.ai，保持聊天页打开，然后重新加载 26Flow 和 Muse.ai 标签页。
- **生成无法开始或看不到媒体：** 检查 Muse.ai 页面和会话状态，然后重试。Muse.ai 可能更改界面或生成流程，这种情况下扩展需要更新。
- **Muse 拒绝生成某个场景：** 26Flow 能识别拒绝回复，包括中文、越南语和英文的“无法创建该场景”或“建议做一个等效版本”的回复，然后用一个接近的、更安全的替代提示词自动重试该场景一次，无需等待确认。重试保留该场景在剧本中的作用和设置；最终能否生成仍由 Muse.ai 决定。
- **时间线导出失败：** 重新加载扩展后再试。MP4 使用内置 FFmpeg 引擎；WebM 使用浏览器的 `MediaRecorder` 和画布捕获。
- **输出与请求的参数不符 / 视频没有声音：** Muse.ai 决定最终生成的媒体；请求的画面比例、音频和视频选项不一定总会被服务采纳。MuseFlow 会要求每个视频节点都带可听见的声音，但如果 Muse 返回的是无声片段，扩展无法凭空为它加上声音——请先在 Muse.ai 标签页里直接播放该片段确认，诊断方法和 FFmpeg 补救办法见中文指南（[使用指南.md](使用指南.md)）。

## Star 历史

<a href="https://www.star-history.com/?repos=bynne2602%2Fmuseflow&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=bynne2602/museflow&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=bynne2602/museflow&type=date&legend=top-left" />
   <img alt="Star 历史图表" src="https://api.star-history.com/chart?repos=bynne2602/museflow&type=date&legend=top-left" />
 </picture>
</a>

## 许可

MuseFlow 采用 [GNU 通用公共许可证 2.0 或更高版本（GPL-2.0-or-later）](LICENSE)，与内置的 FFmpeg 核心一致。FFmpeg 的 JavaScript 封装仍为 MIT 许可。详见[第三方声明](THIRD_PARTY_NOTICES.md)和附带的许可文本。
