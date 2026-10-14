# 视频剪辑与透明动效交付流程

用于口播剪辑、字幕、声音和动效制作的 Agent 工作流。默认沿用当前工程，先完成所有正式素材和同步准备，再一次批量导入剪映素材库，并在 Codex 展示；用户自行拖入和摆放时间线。叠加动效保留真实 Alpha 透明背景，素材首帧有可见主体。

本 skill 明确采用作者的个人交付偏好：默认不备份原片、不制作测试样片、不主动保存工程、不导出最终成片；测试验收由用户负责。它适合接受这些分工的使用者，用户本次明确指令优先。

示例请求：

> 为当前口播视频制作透明重点字幕和提示音，全部素材做好后一次导入剪映，时间线由我摆放。

## 环境与依赖

这是流程 skill，不包含编辑器控制程序、渲染引擎或媒体生成服务。执行前按任务使用已安装且可用的能力；依赖缺失时准确说明能完成的范围。

| 任务 | 按需使用的能力或 skill |
|---|---|
| 剪映控制 | `jianying-editor` 或宿主实际可用的编辑器工具 |
| 可编辑剪映草稿 | `jianying-roughcut-export`，仅明确请求时 |
| 本地媒体处理 | FFmpeg / `ffmpeg-skill` |
| 动画、转场 | `hyperframes-core`、`hyperframes-animation`；创意设计按需用 `hyperframes-creative` |
| 口播画中画 | `talking-head-pip` 或可用的等效布局、蒙版工具 |
| 重点字幕和提示音 | `koubo-cut`；口播包装按需用 `package-talking-head-video` |
| 文案改写 | [short-video-script-skill](https://github.com/yesterising/short-video-script-skill)，交付前按需用 `humanizer-zh` |
| ChatCut | 与当前宿主匹配的插件、技能及工具 |

以上工具和 companion skills 不随本仓库打包，名称不代表已安装。纯字幕文件纠错可独立使用 [srt-script-corrector](https://github.com/yesterising/srt-script-corrector)。

参考经验见 [动效与剪映实战经验](references/motion-and-editor-practice.md)。其中透明编码兼容性来自历史工程，不能视为所有剪映版本均验证通过。

## 安装

将本仓库完整克隆到宿主的 skill 目录，保留文件结构。在 Codex 中可使用：

```bash
git clone https://github.com/yesterising/video-editing-playbook.git "${CODEX_HOME:-$HOME/.codex}/skills/video-editing-playbook"
```

已有同名目录时先处理现有安装，避免覆盖本地定制。安装后让宿主重新加载技能目录，并用自然语言描述目标，或显式调用 `$video-editing-playbook`。其它支持 `SKILL.md` 的 Agent 可使用各自的技能目录；媒体展示和编辑器控制能力取决于宿主。

## 许可

MIT，见 [LICENSE](LICENSE)。
