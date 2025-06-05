<div align="center">

# 🦅 FenixAI Trading Bot v2.7.0

### Autonomous Multi-Agent Cryptocurrency Trading System with Self-Evolving Memory

[![GitHub stars](https://img.shields.io/github/stars/Ganador1/FenixAI_tradingBot?style=flat&logo=github&label=Stars&color=yellow)](https://github.com/Ganador1/FenixAI_tradingBot/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/Ganador1/FenixAI_tradingBot?style=flat&logo=github&label=Forks)](https://github.com/Ganador1/FenixAI_tradingBot/network/members)
[![Ko-fi](https://img.shields.io/badge/Ko--fi-Support_the_project-FF5E5B?logo=ko-fi&logoColor=white)](https://ko-fi.com/ganador)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![LangGraph](https://img.shields.io/badge/Orchestration-LangGraph-green.svg)](https://langchain-ai.github.io/langgraph/)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
[![FastAPI](https://img.shields.io/badge/API-FastAPI-009688.svg)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/Frontend-React_18-61DAFB.svg)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6.svg)](https://www.typescriptlang.org/)
[![Binance](https://img.shields.io/badge/Exchange-Binance_Futures-F0B90B.svg)](https://www.binance.com/)
[![arXiv](https://img.shields.io/badge/arXiv-2509.25140-b31b1b.svg)](https://arxiv.org/abs/2509.25140)
[![TailwindCSS](https://img.shields.io/badge/Styling-TailwindCSS-38B2AC.svg)](https://tailwindcss.com/)
[![Socket.IO](https://img.shields.io/badge/Realtime-Socket.IO-010101.svg)](https://socket.io/)

*An advanced trading system powered by multiple specialized AI agents that collaborate to analyze markets, manage risk, and execute trades on Binance Futures. Features ReasoningBank memory system for self-evolving agent capabilities.*

</div>

> [!WARNING]
> ### 🛡️ FenixAI is 100% free and open source — beware of scams
> FenixAI is free software released under the [Apache 2.0 license](LICENSE). **Nobody sells it, licenses it, or charges for access.** If anyone asks you to pay, "activate" a copy, join a paid group, or deposit funds into any wallet or exchange account to "unlock" Fenix, **it is a scam impersonating this project** — do not send them anything.
>
> The **only** official channels are:
> - 📦 This repository: [github.com/Ganador1/FenixAI_tradingBot](https://github.com/Ganador1/FenixAI_tradingBot)
> - ☕ The project's official Ko-fi: [ko-fi.com/ganador](https://ko-fi.com/ganador)
> - ✉️ Private contact: **hyperionganador@proton.me**
>
> There are **no** official Telegram groups, Discord servers, paid signal channels, or "resellers". Anything else claiming to be FenixAI is not us.

<div align="center">

![Fenix Dashboard Preview](./Dashboard%20Fenix.png)

[📖 Documentation](./docs/) · [🚀 Quick Start](#-quick-start) · [🏗️ Architecture](#-architecture) · [📝 Changelog](./docs/CHANGELOG.md) · [📄 Paper](https://arxiv.org/abs/2509.25140)

</div>

---

> **⚠️ WARNING:** Fenix is under active development, is not yet proven profitable, and may not work as expected. Use at your own risk. Paper trading is strongly recommended before any live deployment.

### 🦅 A Message from the Creator (v2.5)

It has been a few months since v2.0. I've been testing the project 24/7 and brainstorming ways to make Fenix more reliable and capable of making better trades. After extensive testing, I am including in this v2.5 release the changes that have made a real, quantifiable impact on performance. 

Among these improvements are the removal of the Sentiment agent, as well as refining the entry and exit logic with new rules, better indicators, and improved timing for decisions. Another upgrade that has provided a massive boost is **Nanofenix**, which introduces a classical ML model with live training. It acts as a strict filter for trades—preventing us from entering too early or too late—and improves the overall win rate by analyzing more input layers. Fenix now executes fewer trades, but the system is much safer and more confident when deciding on an entry or exit.

### 🌍 Update (July 2026): the Sentiment agent is back — and macro-aware

The Sentiment agent has been reactivated with broader macro context, bounded
source handling, and deterministic risk controls. Private evaluation prompts,
event-level outputs, and operator-specific thresholds are not published.

The new Sentiment stack fixes the root cause:

- **Macro/geopolitical news scanner** (`src/tools/macro_news.py`): world-news RSS feeds (BBC, Al Jazeera, CNBC) filtered by high-impact keywords with word-boundary matching and a `severe`/`high` severity classifier. Fresh high-impact headlines are injected into the sentiment prompt ahead of crypto news.
- **Fear & Greed with day-over-day trend**: the prompt now receives `"20 (yesterday 27, change -7)"` instead of a bare number — a sharp drop flags an active macro shock with causal context.
- **Macro alert rules in the prompt**: a fresh severe event (military strikes, war escalation, major default) justifies NEGATIVE sentiment on its own; stale or mild items only modulate confidence.
- **Deterministic macro risk controls**: configurable safeguards can reduce or
  block exposure during fresh high-severity events.

I will keep testing and improving Fenix. I know I don't push commits very often, but I strongly prefer to test everything exhaustively in a local environment before sharing my findings with you all, just to ensure everything is perfect. 

This version will be available as a new Release. If you prefer to revert to v2.0 (which is highly stable), you will still be able to do so.

Thank you all so much for your massive support!

**Ganador**

---

## ⭐ Star History

<a href="https://star-history.com/#Ganador1/FenixAI_tradingBot&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=Ganador1/FenixAI_tradingBot&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=Ganador1/FenixAI_tradingBot&type=Date" />
   <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=Ganador1/FenixAI_tradingBot&type=Date" />
 </picture>
</a>

---

## ✨ What's New in v2.6 (in development)

> **Data-integrity release** — v2.6 is built around one flagship discovery and fix: live indicators were being computed on partial-candle snapshots instead of closed candles. Everything else hardens the stack around it: smarter NanoFenix self-monitoring, a rebuilt vision pipeline, prompt-injection defenses, and a dashboard that finally shows *why* the engine did (or didn't) trade.

### 🔬 Indicator Integrity (flagship fix)

| Fix | Details |
|-----|---------|
| **Closed-candle indicator buffer** | Indicators use closed candles while partial updates refresh market price only. |
| **REST candle backfill on startup** | The indicator buffer is seeded with the last ~60 closed candles before the WebSocket starts (`FENIX_KLINE_BACKFILL_LIMIT`), so the very first analysis cycle works with a real series instead of warming up on ticks. |
| **Entry-filter observability** | Every blocked entry now logs its exact reason (MTF veto, directional score, min confidence, cooldown…) instead of only emitting a silent frontend event. |
| **Order reconciliation** | Ambiguous order outcomes fail closed and are reconciled before another action is attempted. |

### 🤖 NanoFenix v3.6 — Self-Monitoring Companion

| Feature | Details |
|---------|---------|
| **Drift-triggered retraining** | Page-Hinkley test on normalized forecast error forces an early retrain when the market shifts, instead of waiting for the fixed retrain cadence. A post-retrain cooldown prevents echo firing. |
| **Per-regime meta-labeling** | Signal success is tracked per market regime (TRENDING / CHOP / VOLATILE / DEAD) with exponential decay; the meta-probability gate tightens only in regimes where the signal historically fails. |
| **Safeguards composing** | Drift detection and retrain-quality gates are evaluated together before replacing an active model. |
| **Honest telemetry** | `drift_retrain_count`, `regime_meta_prob` and regime sample counts are reported even on HOLD signals, and surfaced in the dashboard. |

### 👁️ Vision Pipeline Overhaul

| Fix | Details |
|-----|---------|
| **Prompt formatting bug** | The visual prompt contained a literal JSON example with unescaped braces — `str.format()` crashed before the image ever reached the model. |
| **Chart generator accuracy** | The chart labeled an SMA 50 as "EMA 50", had no pivot overlay, and drew a false vertical line from SuperTrend warmup zeros. Now: true EMA 50, R3..S3 pivot levels, NaN warmup. |
| **Chart metadata in the prompt** | The vision model receives the real candle count plus numeric EMA/Bollinger/VWAP/SuperTrend/pivot values alongside the image. |
| **Compact JSON contract** | Single-line, ~300-char response schema with a raised token budget — eliminates truncated-JSON retry loops. |

### 🛡️ Security Hardening

- **Prompt-injection defenses**: scraped news/social content is wrapped as untrusted data (`src/security/prompt_sanitizer.py`) and the sentiment prompt is instructed to never follow instructions embedded in it.
- **Alert config validation**: placeholder Telegram/Discord credentials are detected at startup, and permanently-failing channels disable themselves after a 4xx instead of erroring every cycle.
- **Risk sizing contract**: `approved_size` is explicitly USD notional in the risk prompt, with an automatic base-asset→notional conversion guard in the engine.

### ☁️ LLM Serving — Ollama Cloud Max

- Cloud and local providers can be selected through configuration.
- Provider experiments remain paper-only by default. Private benchmark results,
  prompts, account data, and operator-specific model assignments are not
  published.
- Contributors can use the public benchmark harness with their own isolated
  configuration.

### 📊 Dashboard

- **Execution Flow feed**: live decision → filters → orders timeline, including every veto with its reason.
- **NanoFenix health panel**: dual-horizon accuracy, drift score & forced-retrain count, per-regime meta-probability, paper-trader scoreboard, and readiness with block reasons.
- **Live-session wiring**: engine events reach the dashboard via a Redis bridge (`REDIS_URL`), external companions are detected (no duplicate spawns), and previously-dropped events (filters, positions, trades, NanoFenix policy) are now forwarded.

---

## ✨ What's New in v2.5

> **Reliability-focused release** — v2.5 brings short-timeframe latency work, a complete performance optimisation pass, NanoFenix v3.5 as a first-class companion signal, DeepSeek v4 cloud experiments, and a full suite of live/paper reliability fixes.

### Core Engine & Latency

| Improvement | Details |
|-------------|---------|
| **Hot-path nonblocking (1m/3m/5m)** | Critical path cycle dropped from ~140 ms → **~10–13 ms**. Technical and QABBA agents resolve cache/fallback before building prompts; LLM refreshes run in background. |
| **Paper mode no-REST** | Paper trades no longer initialise `BinanceService` for balance; uses `FENIX_BALANCE_FALLBACK_USDT` to avoid ~1 s spikes per simulated trade. |
| **Parallel agent graph** | Technical, QABBA, Sentiment, and Visual run in true parallel via LangGraph; background caches for charts, news, and balance. |
| **Deterministic risk mode** | `FENIX_RISK_DETERMINISTIC=1` skips the Risk LLM entirely and computes ATR-based SL/TP/size — 15m full pipeline now runs in ~15 s (was ~57 s). |

### Execution Reliability

| Fix | Details |
|-----|---------|
| **Live position hydration** | On restart, if Binance already has an open position, the engine hydrates local state before assuming the account is flat — prevents duplicate entries. |
| **Invalid-price guard** | Paper `trade:simulated` events and hybrid runner reject signals with `price = 0.0` before logging position transitions. |
| **Algo protective order verification** | Order monitor now also checks `openAlgoOrders` (Binance 3xxxxxxx IDs), fixing false `PROTECTION_NOT_VERIFIED` alerts. |
| **Failed execution risk isolation** | Failed live execution attempts no longer count as realized losing trades in the `RuntimeRiskManager` loss-streak counter. |
| **Direction-aware SL/TP validation** | Risk agent validates SL is on the correct side of entry; example-copied BTC-like levels for SOL are replaced with deterministic ATR levels before execution. |
| **Same-side entry prevention** | Engine skips same-side entries after hydration; `FENIX_ALLOW_ADD_TO_POSITION=1` enables intentional pyramiding. |

### NanoFenix v3.5 — Companion Signal

| Feature | Details |
|---------|---------|
| **Adaptive fusion** | `ENABLE_ADAPTIVE_FUSION=1` — multi-horizon blending adapts weights based on per-horizon calibration instead of fixed 0.4/0.6 split. |
| **Fee-aware trailing** | `MIN_TRAILING_NET_PCT` gates trailing exits: position is only closed when estimated net PnL after round-trip fees exceeds the threshold — no more "wins" that lose money to fees. |
| **Configurable hard-veto** | `FENIX_NANOFENIX_HARD_VETO_REASONS` — only critical reasons (direction mismatch, companion not ready, stale signal) unconditionally block execution; soft reasons (`low_pred_bps`) reduce size without blocking. |
| **Companion readiness** | `COMPANION_MIN_DIR_SAMPLES` lowered from 80 → 10, allowing companion activation in the first few hundred bars. |

### Agent Improvements (v2.1)

| Improvement | Details |
|-------------|---------|
| **Tiered trailing stop** | Four profit tiers: 0–1% → 2.0%, 1–2% → 1.0%, 2–3% → 0.5%, >3% → 0.3% trailing. Trailing history tracked per trade. |
| **Risk Manager soft-cap** | Instead of vetoing, the Risk Manager now caps position size to available exposure and approves the trade. |
| **Agent weight rebalance** | Technical/QABBA at 0.35 each; Sentiment at 0.15 as a confidence modulator (reactivated July 2026 with macro awareness), with live agent track records injected so the Decision Agent discounts underperforming agents. |
| **Decision Agent JSON fix** | Prompt payload trimmed to essential fields; timeout reduced 15 s → 12 s; fallback consensus improved. |
| **Sentiment Agent cache** | 15-minute news cache (`_NEWS_CACHE_TTL_SEC=900`); payload and retries reduced for faster fallback. |

### Timeframe-Aware Indicator System

| Feature | Details |
|---------|---------|
| **Per-TF indicator profiles** | Database of 20+ indicators scored by timeframe, market regime, lag, and reliability. |
| **CHOP / Donchian / Keltner** | Choppiness Index drives execution gating; Donchian breakout detection; Keltner Channels for TTM Squeeze. |
| **Advanced indicators** | HMA, Fisher Transform, VWAP bands, Funding Rate extremes, Open Interest trend confirmation, CVD divergences. |
| **Timeframe-aware SL/TP** | Long TF (15m/1h/4h): 4% default SL, 2.0 RR, 2× ATR. Short TF (1m/5m): 2% SL, 1.5 RR, 1.5× ATR. |

### New LLM Integrations

FenixAI supports configurable local and cloud inference providers. No model is
presented as profitable or universally suitable. Evaluate provider and prompt
changes with isolated paper runs using your own data, costs, and risk limits.

See [NanoFenix HTF v2.5 changes](./docs/NANOFENIX_HTF_V2_5_CHANGES.md)
and the [release checklist](./RELEASE_CHECKLIST.md).

---

## ✨ What's New in v2.0

> **Complete architectural overhaul** - Migrated from CrewAI to **LangGraph** for more robust and flexible agent orchestration.

| Feature | v1.0 (June 2025) | v2.0 (December 2025) |
|---------|------------------|---------------------|
| **Orchestration** | CrewAI | LangGraph (State Machine) |
| **Memory System** | Basic TradeMemory | [ReasoningBank](https://arxiv.org/abs/2509.25140) + LLM-as-Judge |
| **Visual Analysis** | Static screenshots | Chart Generator + Playwright TradingView Capture |
| **LLM Providers** | Ollama only | Ollama, MLX, Groq, HuggingFace |
| **Frontend** | Flask Dashboard | React + Vite + TypeScript |
| **Agent Weighting** | Static | Dynamic (performance-based) |
| **Security** | Basic | SecureSecretsManager + Path Validation |
| **Real-time** | Polling | WebSocket + Socket.IO |

### Notable security and developer workflow improvements
- API binds to `127.0.0.1` by default to avoid accidental public exposure. To bind to all interfaces intentionally, set `ALLOW_EXPOSE_API=true`.
- Demo accounts are not seeded by default; set `CREATE_DEMO_USERS=true` for local development.
- `DEFAULT_DEMO_PASSWORD` and `DEFAULT_ADMIN_PASSWORD` may be used for local testing; avoid using them in production.
- We added `DEVELOPMENT.md` and `RELEASE_CHECKLIST.md` to help developers follow the release process and avoid secrets leaks.
- Archived internal reports are now in `docs/archives/reports/` to reduce root clutter.

---

## 🧠 How It Works

FenixAI employs a **multi-agent architecture** where specialized AI agents collaborate to make trading decisions. The system is built on three core pillars:

1. **Multi-Agent Collaboration**: Specialized agents analyze different aspects of the market
2. **Self-Evolving Memory**: ReasoningBank enables agents to learn from past decisions
3. **Dynamic Risk Management**: Real-time circuit breakers and position sizing

### 🧪 ReasoningBank: Self-Evolving Agent Memory

FenixAI implements the **ReasoningBank** architecture based on the research paper ["ReasoningBank: Scaling Agent Self-Evolving with Reasoning Memory"](https://arxiv.org/abs/2509.25140). This novel memory framework:

- **Distills reasoning strategies** from successful and failed trading decisions
- **Semantic retrieval** of relevant historical context during analysis
- **LLM-as-Judge** evaluates decision quality and provides feedback
- **Continuous learning** enables agents to improve over time
- **Embeddings-based search** finds similar market conditions from history

```python
# Example: Agent retrieves relevant context from ReasoningBank
context = reasoning_bank.get_relevant_context(
    agent_name="technical_analyst",
    current_prompt=market_analysis_prompt,
    limit=3
)
# Agent uses historical insights to make better decisions
```

### 📊 Visual Analysis System

The Visual Agent supports two modes for chart analysis:

| Mode | Description | Use Case |
|------|-------------|----------|
| **Chart Generator** | Generates charts with indicators using `mplfinance` | Fast, offline, customizable |
| **Playwright Capture** | Captures TradingView screenshots via browser automation | Real TradingView charts, advanced indicators |

Both modes produce base64-encoded images that are analyzed by vision-capable LLMs (LLaVA, GPT-4V, etc.).

### 🤖 The Agent Team

| Agent | Responsibility | Inputs | Output |
|-------|---------------|--------|--------|
| **Technical Analyst** | RSI, MACD, ADX, SuperTrend, EMA crossovers | OHLCV data, indicators | Signal + confidence |
| **Visual Analyst** | Chart pattern recognition, support/resistance | Generated charts / TradingView screenshots | Pattern analysis |
| **Sentiment Analyst** | News, Twitter, Reddit, Fear & Greed Index | Social feeds, news APIs | Market sentiment |
| **QABBA Agent** | Bollinger Bands, volatility, squeeze detection, OBI, CVD | Microstructure data | Volatility signal |
| **Decision Agent** | Weighted consensus from all agents | All agent reports | Final trade decision |
| **Risk Manager** | Circuit breakers, position sizing, drawdown limits | Portfolio state, decision | Approved/vetoed trade |

### 🔄 Agent Workflow

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│                              FENIX AI v2.5 RC                               │
├─────────────────────────────────────────────────────────────────────────────┤
│