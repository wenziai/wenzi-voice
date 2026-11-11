# 安装、调用与环境适配

本包遵循通用 Agent Skills 结构：一个顶层技能目录、`SKILL.md` 和按需读取的 `references/`。它不依赖外部工具或模型专属语法。

## Codex

### 全局安装

把整个 `wenzi-voice` 文件夹复制到：

```text
~/.agents/skills/wenzi-voice/
```

部分 Codex 环境也识别 `~/.codex/skills/`。若已有固定技能目录，沿用当前环境的目录即可。重新开始会话，让技能元数据重新被发现。

### 项目安装

复制到项目内：

```text
.agents/skills/wenzi-voice/
```

### 调用示例

```text
用 $wenzi-voice 把这段口述整理成一条朋友圈，保留我的重话，不要升华。
```

```text
用 $wenzi-voice 改这篇公众号文章。事实不要新增，结尾到观点讲完就停。
```

Codex 可以根据 `description` 自动发现本技能；显式写 `$wenzi-voice` 最稳定。

## Claude Code

### 全局安装

```text
~/.claude/skills/wenzi-voice/
```

### 项目安装

```text
.claude/skills/wenzi-voice/
```

安装后开启新会话，再明确要求使用 `wenzi-voice`。若所在版本不支持技能自动发现，可让 Claude 先读取 `wenzi-voice/SKILL.md`，再执行写作任务。

## 其他 Agent 或普通聊天环境

优先使用支持 Agent Skills / `SKILL.md` 的技能目录。若环境不支持：

1. 将 `SKILL.md` 作为主指令；
2. 同时提供 `references/style-guide.md`；
3. 改写任务再提供 `references/examples.md`；
4. 用户返回最终稿时提供 `references/calibration.md`。

不要一次把所有参考文件塞进上下文。按任务读取，能减少模板化和规则互相干扰。

## 更新方式

日常校准优先追加 `references/calibration-log.md`，不要频繁扩写主 `SKILL.md`。只有当同一偏好被明确确认，且会改变大多数任务的判断时，才把它提升到风格指南或主入口。

## 格式依据

- OpenAI Skills 说明：<https://developers.openai.com/plugins/concepts/skills>
- OpenAI 官方安装目录示例（同时列出 Codex 与 Claude Code）：<https://developers.openai.com/api/reference/cli>

以上路径核验日期：2026-11-11。不同版本或托管环境可能使用自己的技能目录，以该环境的官方说明为准。

