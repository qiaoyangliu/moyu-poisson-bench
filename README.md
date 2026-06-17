# Poisson Bench

A single-file, in-browser football betting model based on **Double Poisson + Dixon-Coles**. Fit team strengths from past results, read the full scoreline distribution, and compare model probabilities against bookmaker odds to compute expected value (EV) for every market.

一个单文件、纯浏览器运行的足球投注模型,基于**双泊松 + Dixon-Coles**。从历史比赛结果拟合球队强度,读取完整比分分布,并把模型概率与庄家赔率对比,算出每个盘口的期望值(EV)。

> ⚠️ **Educational / analytical tool only.** The output is only as good as the λ you feed it, and a hand-tuned model is unlikely to beat a bookmaker's pricing. Use it to understand odds structure and probability — not as a money-making system. Follow your local laws and gamble responsibly.
>
> ⚠️ **仅供学习与分析。** 模型输出的可靠性完全取决于你提供的 λ,手调模型几乎不可能跑赢庄家定价。请把它当作理解赔率结构与概率的工具,而非赚钱系统。请遵守当地法律,理性投注。

---

## Features / 功能

- **Dixon-Coles fit from data / 从数据拟合** — paste recent results; the app estimates each team's attack/defense and home advantage via weighted Poisson regression, and estimates ρ from low-score residuals. 粘贴近期结果,程序用加权泊松回归估出攻防强度与主场优势,并由低比分残差估出 ρ。
- **Scoreline probability matrix / 比分概率矩阵** — the full bivariate distribution as a heatmap. 完整的二维比分分布热力图。
- **Markets & EV / 盘口与 EV** — 1X2, totals, team goals, Asian handicap, BTTS; type American odds to get implied probability, edge and EV per $1. 1X2、大小球、球队进球、让球、双方进球;填入美式赔率即得隐含概率、edge 和每 $1 期望值。
- **λ sensitivity / λ 敏感性** — see how each market shifts as λ moves ±0.30. 查看 λ 浮动 ±0.30 时各盘口的变化。
- **Bilingual / 中英双语** — toggle between English and 中文 with one click. 一键切换中英文。
- **AI data prompt / AI 取数提示词** — a built-in prompt that instructs a web-connected AI to fetch correctly formatted, verified results. 内置提示词,引导联网 AI 抓取格式正确、经核实的数据。
- **No backend, no build, no dependencies** — one HTML file, runs entirely in the browser. 无后端、无构建、无依赖,单个 HTML 文件,全程浏览器运行。

---

## Usage / 使用

1. **(Recommended) Fit λ from data.** Paste recent results from the teams' league/competition, click **Fit**, pick home/away, then **Apply to model**. 先用数据拟合:粘贴两队所在赛事的近期结果,点「拟合」,选好主客队,再点「代入模型」。
2. Or set λ manually with the sliders. 或用滑块手动设 λ。
3. Type the bookmaker's **American odds** into each market to compute EV. 在各盘口填入庄家**美式赔率**算 EV。
4. Green **+EV** = positive expected value under the model; red **SKIP** = negative. 绿色 **+EV** = 模型下正期望;红色 **SKIP** = 负期望。

The math and a full user guide are at the bottom of the page. 数学原理与完整说明书在页面底部。

### Data format / 数据格式

```
home, away, home goals, away goals, date(optional YYYY-MM-DD)
Arsenal, Chelsea, 2, 1, 2026-05-24
```

> **Note / 说明:** Strength fitting is most reliable *within one league/competition* (teams share opponents and are on the same scale). For cross-league or international matchups (e.g. World Cup), the relative scale is less reliable — prefer manual λ there. 强度拟合在**同一联赛/赛事内**最可靠(球队有共同对手、尺度一致)。跨联赛或国家队对决(如世界杯)相对尺度不可靠,这类情况更适合手填 λ。

---

## Tech / 技术

Plain HTML + CSS + vanilla JavaScript. No frameworks, no external runtime dependencies (web fonts load from a CDN and fall back to system fonts offline). All computation runs locally in the browser; no data is sent anywhere.

纯 HTML + CSS + 原生 JavaScript。无框架、无外部运行时依赖(字体走 CDN,离线时回落系统字体)。所有计算在本地浏览器完成,不向任何服务器发送数据。

## License / 许可

MIT — do what you like, no warranty. MIT 许可,自由使用,不提供任何担保。
