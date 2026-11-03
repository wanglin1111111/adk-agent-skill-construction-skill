# ADK 智能体 Skill 构建技能包

基于 Google ADK（Agent Development Kit）**渐进式披露架构**的 AI Agent Skill 构建方法，覆盖从内联 Skill 到 Skill 工厂的 8 个核心技能。

## 解决什么问题

给 Agent 挂载大量 Skill 时，上下文会被迅速吃满。ADK 的 SkillToolset 让 Agent 按需加载领域知识：10 个 Skill 的传统方式约消耗 10000 token，渐进式披露后 L1 仅约 1000 token，**最多可降低 90% 的基础上下文消耗**。

## 核心技能

| # | 技能 | 要点 |
| --- | --- | --- |
| 1 | 渐进式披露架构 | L1 元数据（约 100 token）→ L2 指令（≤5000 token）→ L3 资源文件，按需激活 |
| 2 | 内联 Skill 构建 | 名称 + 描述 + 指令三字段，适合快速原型与 10 行以内的简单规则 |
| 3 | 文件型 Skill 构建 | `SKILL.md` + `references/` + `assets/`，可独立版本管理与跨 Agent 复用 |
| 4 | 外部 Skill 导入 | 兼容 agentskills.io 规范，Gemini CLI / Claude Code / Cursor 等 40+ 产品支持 |
| 5 | Skill 工厂（元 Skill） | 让 Agent 生成新的 SKILL.md，实现自我扩展 |
| 6 | Skill 描述优化 | description 是 Agent 决策的核心依据，必须具体可判别 |
| 7 | Agent 评估与测试 | 功能、覆盖、冗余、资源、边界五类测试，自动生成的 Skill 保留人工审核 |
| 8 | 过早优化规避 | 一律从内联开始，需要引用外部文档或跨 Agent 复用时再升级为文件型 |

## 目录结构

```
.
├── SKILL.md   # 完整技能说明（8 个技能 + 关键洞察）
└── LICENSE    # MIT
```

## 使用方式

把本目录放入 Agent 的 skills 目录，或直接将 `SKILL.md` 作为技能指令加载。外部 Skill 可通过社区仓库安装，例如：

```bash
npx skills add google/adk-docs -y -g
```

## 适用对象

AI Agent 开发者、希望控制上下文成本的后端/平台工程师、对 ADK 架构感兴趣的团队。

## 许可

MIT