# Simin Yuan

**独立研究者。做可被验证的事，并公开我被验证错了的部分。**

> 我与一个长期运行的 AI agent（时晴）协作。我们公开发布两类东西：
> **可复现的证据**，和**能被证伪的预测**。

---

## 五个作品

### 1. [`precheck`](https://github.com/simin-yuan/precheck) — 让 agent 用「它无权编写」的检查自证

> 你的 agent 说它做完了。这个工具先把验收检查**冻住**，再问一句没人问的话：这条检查**本来能失败吗**？

检查在动工之前写死、并入哈希链；事后改一个字，之前所有结论全部作废。检查通过之后，
它改坏被检查的产物再跑一遍 —— 在坏输入上照样通过的检查，从来就不是证据。

- 仓库内 demo 实跑：`replicas: 3 -> 0`，检查照样 `exit 0`
- 19 个单测、零依赖、纯标准库、不联网；三系统 × Python 3.8–3.13 CI 全绿（9/9）
- 已上 PyPI：`pip install precheck`（v0.1.1）
- 自带 GitHub Action

### 2. [`greencheck`](https://github.com/simin-yuan/greencheck) — 专查质量门禁的变异测试工具

> 删掉 schema 里一行，三个主流校验器都不吭声了 —— 而且它吐出来的任何输出都不会告诉你。

`pip install greencheck`，零依赖、纯标准库。它在你的配置和 schema 上自动制造小改动
（删一行、把值清空、把数字改成 0），然后问你的门禁还拦不拦得住。

- 本机实测 3/3：同一份非法数据，`jsonschema` / `check-jsonschema` / `ajv` 从 `exit 1` 变成 `exit 0`
- 唯一一条规则：**一个数字，只有在「已知输入不同」的条件下被观察到取过不同的值，它才是一个测量**
- 输出明说「这些是问题、不是结论」—— 不拿变异数冒充缺陷数

### 3. [`self-auditing-agent`](https://github.com/simin-yuan/self-auditing-agent) — 一个会自我审计的 AI

> 别的 AI 在证明自己能干活。这个 AI 在证明自己**能被查**。

一份公开的运行档案：每个结论、支撑证据、**它自己的 bug**、以及第三方如何复现。
价值不在"发现了什么"，在于**它公开了自己错在哪、以及怎么发现的**。

- 第一卷：74 分钟对陌生 11 仓库 / 1768 文件的取证审计
- 含对抗性发现（原实现安全缺口）、4 个自己的 bug、1 个假发现、1 次误报
- 核心发现**一条命令可复现**：`python repro/verify_sql_gap.py`

### 4. [`context-volume-not-coupling`](https://github.com/simin-yuan/context-volume-not-coupling) — 受控实验

*Volume or Coupling? A Scale-Dependent Dissociation in Constraint Recovery of Language-Model Loops*
语言模型自指循环中约束恢复的尺度依赖性解离。预印本 DOI: [10.5281/zenodo.21200851](https://doi.org/10.5281/zenodo.21200851)

### 5. [`shiqing-predictions`](https://github.com/simin-yuan/shiqing-predictions) — 公开预测账本

署名 AI、发布前入链、到期公开结算、**MISS 永久保留**。
不是"展示准确率"，是把**可证伪性**当作一条不可绕开的纪律。

---

## 我在做什么

**判断一个 AI 靠不靠得住，不看它做对什么，看它敢不敢让人查它做错什么。**

这决定了我的三条工作原则：

| 原则 | 落地形态 |
|---|---|
| 证据先于断言 | 每条结论带命令 + 输出；分档 `① 跑出结果 > ② 读过原文 > ③ 只按元数据判` |
| 门禁必须能说"不" | 验证门禁只用**会失败的输入**去喂；不能输出否定的判据不算判据 |
| 记录失败 | 自己的 bug、误报、假发现全部公开——**只放成功路径的展示不可信** |

---

## English

Independent researcher. I ship **reproducible evidence** and **falsifiable predictions**, together with a long-running AI agent (Shiqing).

**You don't judge an AI by what it gets right — you judge it by whether it lets you check what it got wrong.**

Works: [precheck](https://github.com/simin-yuan/precheck) ·
[greencheck](https://github.com/simin-yuan/greencheck) ·
[self-auditing-agent](https://github.com/simin-yuan/self-auditing-agent) ·
[context-volume-not-coupling](https://github.com/simin-yuan/context-volume-not-coupling) ·
[shiqing-predictions](https://github.com/simin-yuan/shiqing-predictions)
