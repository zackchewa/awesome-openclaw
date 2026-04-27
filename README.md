<p align="center">
  <a href="https://github.com/openclaw/openclaw">
    <picture>
      <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.svg">
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.svg">
      <img alt="OpenClaw" src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.svg" width="600">
    </picture>
  </a>
</p>

<h1 align="center">Awesome OpenClaw</h1>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/stargazers"><img src="https://img.shields.io/github/stars/openclaw/openclaw?style=flat&logo=github&label=Stars&color=gold" alt="Stars"></a>
  <a href="https://github.com/openclaw/openclaw/releases"><img src="https://img.shields.io/github/v/release/openclaw/openclaw?include_prereleases&label=Release&color=orange" alt="Release"></a>
  <a href="https://github.com/openclaw/openclaw/blob/main/LICENSE"><img src="https://img.shields.io/github/license/openclaw/openclaw?color=blue" alt="License"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/badge/Discord-Claw%20Crew-5865F2?logo=discord&logoColor=white" alt="Discord"></a>
  <br>
  <em>A curated, source-backed index for OpenClaw resources, docs, plugins, ecosystem projects, and community learning.</em>
</p>

---

**OpenClaw** is a self-hosted personal AI assistant and multi-channel gateway. You run one Gateway on your own machine or server; it connects chat apps, WebChat, Control UI, companion apps, mobile nodes, plugins, model providers, tools, sessions, and multi-agent routing into one always-available assistant.

This repository is a community-maintained resource index for OpenClaw. It is not the official OpenClaw documentation. For installation, configuration, security, and release details, prefer the official sources linked below.

## Contents

- [Official sources](#official-sources)
- [What OpenClaw is today](#what-openclaw-is-today)
- [Quick start](#quick-start)
- [Architecture map](#architecture-map)
- [Core capabilities](#core-capabilities)
- [Use cases and operating patterns](#use-cases-and-operating-patterns)
- [Plugins and integrations](#plugins-and-integrations)
- [Ecosystem resources](#ecosystem-resources)
- [Learning resources](#learning-resources)
- [Security and operations](#security-and-operations)
- [Current update themes](#current-update-themes)
- [Maintenance pattern](#maintenance-pattern)
- [Community and contribution](#community-and-contribution)
- [Archived material](#archived-material)

## Official sources

| Resource | Link | Notes |
|---|---|---|
| OpenClaw website | [openclaw.ai](https://openclaw.ai/) | Product homepage, quick start, integrations, showcase, and blog. |
| Official repo | [github.com/openclaw/openclaw](https://github.com/openclaw/openclaw) | Source code, issues, releases, changelog, and contribution workflow. |
| Official docs | [docs.openclaw.ai](https://docs.openclaw.ai/) | Installation, channels, plugins, Gateway, Control UI, nodes, and concepts. |
| Upstream tags | [GitHub tags](https://github.com/openclaw/openclaw/tags) | Current version tags and beta tags. |
| Integrations | [openclaw.ai/integrations](https://openclaw.ai/integrations) | Current public integration list. |
| Showcase | [openclaw.ai/showcase](https://openclaw.ai/showcase) | Examples of what people are building. |
| Use cases directory | [openclawsearch.com/use-cases](https://openclawsearch.com/use-cases) | Community-maintained practical use-case map. |
| Automation docs | [docs.openclaw.ai/automation](https://docs.openclaw.ai/automation) | Cron, webhooks, Gmail Pub/Sub, heartbeat, and background tasks. |
| Discord | [discord.gg/clawd](https://discord.gg/clawd) | Community discussion. |

## What OpenClaw is today

OpenClaw is best understood as two things together:

1. **A personal assistant you run yourself.** It can respond from the channels and devices you already use.
2. **A Gateway/control plane.** The Gateway connects channels, plugins, sessions, routing, tools, model providers, and surfaces.

The current official docs emphasize:

- self-hosting and user-controlled data;
- one Gateway process that connects built-in channels and plugin channels;
- WebChat, Control UI, companion apps, and mobile/headless nodes;
- multi-agent routing with isolated sessions, workspaces, and auth scopes;
- plugin-based capabilities for channels, model providers, speech, media, browser, search, memory, observability, and automation.

## Quick start

Use the official docs as the source of truth. Current upstream guidance is:

```bash
npm install -g openclaw@latest
openclaw onboard --install-daemon
openclaw dashboard
```

Runtime guidance from current docs:

- Node 24 is recommended.
- Node 22 LTS `22.14+` is also supported.
- Docker is available, but it is not the only or primary path.

Useful docs:

- [Getting started](https://docs.openclaw.ai/start/getting-started)
- [Node setup](https://docs.openclaw.ai/install/node)
- [Updating](https://docs.openclaw.ai/install/updating)
- [Docker](https://docs.openclaw.ai/install/docker)

## Architecture map

| Layer | What it does | Useful docs |
|---|---|---|
| Gateway | Single source of truth for sessions, routing, channel connections, plugin loading, and HTTP/WebSocket surfaces. | [Docs home](https://docs.openclaw.ai/) |
| Channels | Connect chat apps and message surfaces such as Telegram, WhatsApp, Discord, Slack, Signal, iMessage, Matrix, Teams, Zalo, Feishu, and more. | [Channels](https://docs.openclaw.ai/channels) |
| Surfaces | WebChat, Control UI, companion app, mobile nodes, CLI, and chat apps. | [Control UI](https://docs.openclaw.ai/web/control-ui), [Nodes](https://docs.openclaw.ai/nodes) |
| Agents and routing | One or many isolated agents with separate workspaces, sessions, state, and channel accounts. | [Multi-agent](https://docs.openclaw.ai/concepts/multi-agent) |
| Plugins | Manifest-backed capability packages for providers, channels, tools, speech, media, memory, observability, and automation. | [Plugins](https://docs.openclaw.ai/tools/plugin) |
| Tools and capabilities | Browser, shell, files, web fetch/search, media understanding, image/video/music generation, diagnostics, skills, and provider-specific tools. | [Tools](https://docs.openclaw.ai/tools), [Skills](https://docs.openclaw.ai/tools/skills) |
| Automation | Scheduled jobs, webhooks, Gmail Pub/Sub, heartbeat turns, and task records that make OpenClaw useful beyond direct chat. | [Automation](https://docs.openclaw.ai/automation), [Cron jobs](https://docs.openclaw.ai/automation/cron-jobs), [Webhooks](https://docs.openclaw.ai/automation/webhook) |

## Core capabilities

| Capability | Current direction |
|---|---|
| Multi-channel assistant | One assistant reachable from multiple chat apps and web/mobile surfaces. |
| Control UI | Browser-based dashboard for chat, configuration, sessions, nodes, access, and runtime status. |
| Multi-agent routing | Run multiple isolated agents, workspaces, and channel accounts through one Gateway. |
| Plugins | Current OpenClaw leans heavily on plugin manifests, plugin registry behavior, and capability surfaces. |
| Voice and TTS | Rapidly expanding TTS, speech, realtime voice, and voice-note support across providers and channels. |
| Browser automation | Safer browser automation, role snapshots, CDP readiness, tab handling, and browser doctor checks. |
| Observability | OpenTelemetry and Prometheus-oriented diagnostics for model calls, token usage, tools, delivery, context, memory pressure, and more. |
| Mobile and nodes | iOS/Android/headless nodes for media, device, and mobile-adjacent workflows. |
| Automation | Cron jobs, webhooks, Gmail Pub/Sub, heartbeat turns, and background task records for recurring or event-driven work. |
| Skills and ClawHub | Workspace, per-agent, personal, managed, bundled, and registry-installed skills with load-time filters and safety checks. |
| Memory and knowledge | Active memory, Memory Wiki, QMD memory, built-in memory tools, and optional external memory backends. |
| Model operations | Model provider setup, auth profile rotation, model fallback, session overrides, and diagnostics for failed calls. |
| Remote access | WebChat, Control UI pairing, Tailscale Serve/Funnel, trusted proxy modes, and device approvals for remote operation. |

## Use cases and operating patterns

OpenClaw is not only a list of channels. The useful pattern is: a user talks through an existing surface, the Gateway routes to the right agent/session, and the agent uses bounded tools, memory, skills, plugins, and approvals to finish real work.

| Pattern | What it looks like | Useful starting points |
|---|---|---|
| Mobile personal assistant | Ask from Telegram, WhatsApp, Discord, Slack, WebChat, or a phone while the Gateway runs elsewhere. | [Channels](https://docs.openclaw.ai/channels), [WebChat](https://docs.openclaw.ai/web/webchat), [Control UI](https://docs.openclaw.ai/web/control-ui) |
| Personal operating system | Daily briefings, calendar prep, reminders, notes, tasks, invoices, email triage, and family/home planning. | [Showcase](https://openclaw.ai/showcase), [Integrations](https://openclaw.ai/integrations), [Cron jobs](https://docs.openclaw.ai/automation/cron-jobs) |
| Developer and repo operations | Issue triage, code review, PR preparation, deploy checks, infra fixes, and long-running coding sessions from chat. | [Agent tools](https://docs.openclaw.ai/plugins/agent-tools), [Subagents](https://docs.openclaw.ai/tools/subagents), [Multi-agent routing](https://docs.openclaw.ai/concepts/multi-agent) |
| Event-driven automation | Scheduled reports, webhooks, email-triggered runs, heartbeat checks, and background tasks with delivery targets. | [Automation](https://docs.openclaw.ai/automation), [Cron jobs](https://docs.openclaw.ai/automation/cron-jobs), [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub) |
| Multi-agent fleet | Separate agents for work, personal, coding, operations, family, or clients with isolated workspace, auth, and sessions. | [Multi-agent routing](https://docs.openclaw.ai/concepts/multi-agent), [Agents CLI](https://docs.openclaw.ai/cli/agent), [Sandbox tools](https://docs.openclaw.ai/tools/multi-agent-sandbox-tools) |
| Voice and phone workflows | Voice wake, voice notes, realtime talk, inbound/outbound calls, and spoken summaries routed back into normal agent sessions. | [Voice wake](https://docs.openclaw.ai/nodes/voicewake), [Voice Call](https://docs.openclaw.ai/plugins/voice-call), [Text-to-speech](https://docs.openclaw.ai/tools/tts) |
| Media and device workflows | Camera, images, files, browser state, screenshots, mobile nodes, and media understanding in normal chat loops. | [Nodes](https://docs.openclaw.ai/nodes), [Media understanding](https://docs.openclaw.ai/nodes/media-understanding), [Browser](https://docs.openclaw.ai/tools/browser) |
| Memory and knowledge systems | Recall, knowledge pages, project memory, session history, Obsidian-style workflows, and reusable skills. | [Memory](https://docs.openclaw.ai/concepts/memory), [Active memory](https://docs.openclaw.ai/concepts/active-memory), [Skills](https://docs.openclaw.ai/tools/skills) |
| Operations and observability | Token/cost metrics, model-call traces, queue health, delivery failures, memory pressure, and support bundles. | [OpenTelemetry](https://docs.openclaw.ai/gateway/opentelemetry), [Prometheus](https://docs.openclaw.ai/gateway/prometheus), [Diagnostics](https://docs.openclaw.ai/gateway/diagnostics) |

See the website page for a more reader-friendly map: [OpenClaw use cases](https://openclawsearch.com/use-cases).

## Plugins and integrations

Current upstream contains more than 100 plugin/extension directories. Present the ecosystem by capability instead of as one flat list.

### Channels and messaging

Discord, Telegram, WhatsApp, Slack, Signal, iMessage, Matrix, Microsoft Teams, Google Chat, Feishu, Zalo, QQBot, Nostr, Twitch, IRC, Mattermost, Synology Chat, Nextcloud Talk, Tlon, LINE, and related channel/runtime packages.

Community additions at the end of this category:

- [feishu-inout](https://github.com/joe960913/feishu-inout) - Lark/Feishu docs, messaging, calendar, and bitable integration for AI coding agents.
- [Nylas OpenClaw plugin](https://www.npmjs.com/package/@nylas/openclaw-nylas-plugin) - email, calendar, and contacts tools across major providers.
- [discourse-openclaw](https://github.com/pranciskus/discourse-openclaw) - Discourse forum read/search/write integration.

### Model providers and agent runtimes

OpenAI, Anthropic, Anthropic Vertex, OpenRouter, Google, xAI, DeepSeek, Qwen, Groq, Mistral, Cerebras, Together, Fireworks, Ollama, LM Studio, vLLM, SGLang, LiteLLM, Amazon Bedrock, Hugging Face, Moonshot, Kimi Coding, Codex, OpenCode, Kilocode, Copilot Proxy, Vercel AI Gateway, Cloudflare AI Gateway, Venice, Z.ai, and others.

### Voice, TTS, speech, and calling

Azure Speech, ElevenLabs, Deepgram, Inworld, Local CLI TTS, Minimax, Volcengine, Xiaomi, Talk Voice, speech core packages, realtime voice/calling plugins, and provider-specific speech integrations.

Community additions at the end of this category:

- [clawr.ing](https://clawr.ing) - phone/calling surface for OpenClaw-style voice workflows.

### Search, web, browser, and extraction

Browser, Brave, DuckDuckGo, Exa, Firecrawl, Perplexity, SearxNG, Tavily, Web Readability, and web fetch/search capability surfaces.

### Memory and knowledge

Active memory, Memory Wiki, LanceDB-backed memory, Voyage embeddings, and related knowledge/memory tooling.

### Media generation and understanding

Comfy, Fal, Runway, Gradium, image generation core, video generation core, media understanding core, and provider-specific media tools.

Community additions at the end of this category:

- [prompt-to-asset](https://github.com/MohamedAbdallah-14/prompt-to-asset) - image-generation routing through one MCP-style interface.

### Observability, diagnostics, and QA

OpenTelemetry diagnostics, Prometheus diagnostics, QA Lab, QA Matrix, synthetic/test plugins, and token/trace-related diagnostics.

Community additions at the end of this category:

- [Manifest](https://github.com/mnfst/manifest) - local cost and model-usage observability for agents.

### Automation, productivity, and operating-system integrations

Cron jobs, webhooks, Gmail Pub/Sub, GitHub, notes, tasks, calendars, browser automation, 1Password, weather, smart-home tools, and OS-specific helpers are now part of the practical OpenClaw surface. Keep these grouped by job-to-be-done instead of treating each integration as a separate category.

Useful docs:

- [Automation overview](https://docs.openclaw.ai/automation)
- [Cron jobs](https://docs.openclaw.ai/automation/cron-jobs)
- [Webhooks](https://docs.openclaw.ai/automation/webhook)
- [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub)
- [Browser tools](https://docs.openclaw.ai/tools/browser)
- [OpenClaw integrations](https://openclaw.ai/integrations)

## Ecosystem resources

High-confidence resources to start with:

| Resource | Link | Why it belongs |
|---|---|---|
| Official integrations | [openclaw.ai/integrations](https://openclaw.ai/integrations) | Current public integration surface. |
| Official showcase | [openclaw.ai/showcase](https://openclaw.ai/showcase) | Real examples from users and builders. |
| Plugin docs | [docs.openclaw.ai/tools/plugin](https://docs.openclaw.ai/tools/plugin) | Canonical plugin model and install/config rules. |
| Multi-agent docs | [docs.openclaw.ai/concepts/multi-agent](https://docs.openclaw.ai/concepts/multi-agent) | Current routing and isolation model. |
| Control UI docs | [docs.openclaw.ai/web/control-ui](https://docs.openclaw.ai/web/control-ui) | Current browser dashboard surface. |
| Upstream tags | [github.com/openclaw/openclaw/tags](https://github.com/openclaw/openclaw/tags) | Current version and beta tags. |
| OpenClaw introduction | [openclaw.ai/blog/introducing-openclaw](https://openclaw.ai/blog/introducing-openclaw) | Naming/history and current project framing. |
| Peter Steinberger on OpenClaw | [steipete.me/posts/2026/openclaw](https://steipete.me/posts/2026/openclaw) | Project context and origin notes. |

Community additions, kept at the end instead of elevated above official sources:

| Resource | Link | Why it belongs |
|---|---|---|
| Onepilot | [onepilotapp.com](https://onepilotapp.com) | iOS/iPadOS companion app for deploying, running, and chatting with remote agents. |
| openclaw-mcp | [GitHub](https://github.com/freema/openclaw-mcp), [website](https://openclaw-mcp.cloud), [npm](https://www.npmjs.com/package/openclaw-mcp) | MCP bridge and packaging links for OpenClaw workflows. |
| Awesome OpenClaw Personas | [GitHub](https://github.com/TravisLeeeeee/awesome-openclaw-personas) | Persona package collection for OpenClaw-style agents. |
| Awesome OpenClaw Agents | [GitHub](https://github.com/mergisi/awesome-openclaw-agents) | Agent template collection for OpenClaw-style workflows. |
| TurboStarter OpenClaw Kit | [turbostarter.dev/openclaw](https://www.turbostarter.dev/openclaw) | Starter kit/boilerplate for OpenClaw-adjacent applications. |
| Awesome OpenClaw Use Cases | [GitHub](https://github.com/hesamsheikh/awesome-openclaw-usecases) | Community-maintained use-case list for practical OpenClaw workflows. |
| OpenClaw Directory | [openclawdir.com](https://openclawdir.com/) | Community directory for discovering projects, plugins, jobs, and examples. |
| Agent Control OpenClaw Plugin | [GitHub](https://github.com/agentcontrol/openclaw-plugin) | Example of policy/control gating around agent actions. |
| OpenViking OpenClaw Plugin guide | [GitHub](https://github.com/volcengine/OpenViking/blob/main/examples/openclaw-plugin/INSTALL-AGENT.md) | Guide for wiring OpenClaw into long-running context/agent systems. |

## Learning resources

Use this section for stable, high-signal learning material. Prefer official docs, talks, and tutorials that are recently verified.

- [Getting started](https://docs.openclaw.ai/start/getting-started)
- [Plugins](https://docs.openclaw.ai/tools/plugin)
- [Control UI](https://docs.openclaw.ai/web/control-ui)
- [Multi-agent routing](https://docs.openclaw.ai/concepts/multi-agent)
- [Updating](https://docs.openclaw.ai/install/updating)
- [Automation](https://docs.openclaw.ai/automation)
- [Cron jobs](https://docs.openclaw.ai/automation/cron-jobs)
- [WebChat](https://docs.openclaw.ai/web/webchat)
- [Skills](https://docs.openclaw.ai/tools/skills)
- [Memory](https://docs.openclaw.ai/concepts/memory)
- [Model providers](https://docs.openclaw.ai/providers/models)
- [Model failover](https://docs.openclaw.ai/concepts/model-failover)
- [OpenTelemetry](https://docs.openclaw.ai/gateway/opentelemetry)
- [Prometheus](https://docs.openclaw.ai/gateway/prometheus)
- [Release policy](https://docs.openclaw.ai/reference/RELEASING)

## Security and operations

OpenClaw is powerful because it can connect to real accounts, local machines, tools, browsers, files, and model providers. Treat setup like local infrastructure, not a toy chatbot.

Good defaults:

- keep OpenClaw updated;
- prefer official docs for install and upgrade paths;
- restrict channel access with allowlists or pairing;
- use strong current-generation models for safety-sensitive workflows;
- review plugin sources before installing unknown packages;
- keep API keys and chat tokens out of public configs;
- use Control UI and diagnostics to inspect runtime state;
- approve new browser/device access intentionally;
- use Tailscale, trusted proxy, or password/token modes deliberately for remote access;
- separate agents by workspace, auth profile, and session store when using multi-agent setups;
- use sandbox/tool policy/elevated-mode docs before giving agents broad local access;
- avoid publishing private workspace, memory, or export data.

Useful links:

- [Updating](https://docs.openclaw.ai/install/updating)
- [Plugins](https://docs.openclaw.ai/tools/plugin)
- [Automation](https://docs.openclaw.ai/automation)
- [Cron jobs](https://docs.openclaw.ai/automation/cron-jobs)
- [WebChat](https://docs.openclaw.ai/web/webchat)
- [Skills](https://docs.openclaw.ai/tools/skills)
- [Memory](https://docs.openclaw.ai/concepts/memory)
- [Model providers](https://docs.openclaw.ai/providers/models)
- [Model failover](https://docs.openclaw.ai/concepts/model-failover)
- [OpenTelemetry](https://docs.openclaw.ai/gateway/opentelemetry)
- [Prometheus](https://docs.openclaw.ai/gateway/prometheus)
- [Release policy](https://docs.openclaw.ai/reference/RELEASING)
- [Control UI device pairing](https://docs.openclaw.ai/web/control-ui)
- [Tailscale remote access](https://docs.openclaw.ai/gateway/tailscale)
- [Sandboxing](https://docs.openclaw.ai/gateway/sandboxing)
- [Sandbox vs tool policy vs elevated](https://docs.openclaw.ai/gateway/sandbox-vs-tool-policy-vs-elevated)

Community additions at the end of this category:

- [OneCLI](https://github.com/johnnyfish/onecli) - credential vault/gateway pattern for keeping raw secrets away from agents.
- [ShellWard](https://github.com/jnMetaCode/shellward) - bilingual prompt-injection and data-exfiltration guardrails.
- [leashed](https://github.com/dormstern/leashed) - policy engine, audit log, and kill switch patterns for agents.
- [SupaClaw](https://github.com/vincenzodomina/supaclaw) - Supabase-first deployment pattern for constrained OpenClaw-style agents.
- [unslop](https://github.com/MohamedAbdallah-14/unslop) - output-cleanup utility for removing common AI writing artifacts before publishing.

## Current update themes

OpenClaw moves fast, so treat this section as a snapshot of current themes rather than a permanent product description. Recent upstream docs, tags, and source structure point to these areas:

- Gateway-first operation across chat apps, WebChat, Control UI, mobile nodes, and remote access.
- Automation surfaces: cron, webhooks, Gmail Pub/Sub, heartbeat turns, task records, and delivery/failure handling.
- Plugin lifecycle hardening: install, startup isolation, stale config repair, bundled dependency repair, ClawHub/npm resolution, and plugin package contracts.
- Skills and memory: skill loading precedence, ClawHub skills, active memory, Memory Wiki, QMD memory, and safer session recall.
- Voice and realtime interaction: voice wake, voice notes, Talk mode, voice-call plugins, streaming transcription, and TTS provider routing.
- Model operations: provider onboarding, auth profiles, model fallback, live switching, cooldowns, and failure summaries.
- Observability: OpenTelemetry, Prometheus, token/cost metrics, model-call traces, queue metrics, delivery outcomes, and memory pressure.
- Browser and tool safety: Browser Doctor, remote browser control, sandbox/tool policy/elevated-mode separation, and scoped multi-agent tools.

For exact behavior, verify against [official docs](https://docs.openclaw.ai/), [upstream tags](https://github.com/openclaw/openclaw/tags), and the current source tree.

## Maintenance pattern

This repo should be maintained as a current map, not a frozen launch-era README. Use this pattern for future updates:

1. Start from official docs, integrations, showcase, upstream tags, and inspectable public repos. Treat social/search mentions as leads only.
2. Add resources only when the source is concrete: docs page, GitHub repo, npm/package page, public guide, or live directory.
3. Organize by jobs and capabilities: channels, agents, automation, memory, voice, model providers, observability, security, and use cases.
4. Keep community additions at the end of the most relevant section unless they become official or widely referenced.
5. Avoid stale launch claims, star-count claims, pricing tables, unsupported growth claims, and marketing copy.
6. Prefer small PRs: README capability map, directory resources, use-case page, validation/routing, archive cleanup.
7. Preserve contributor credit by merging useful contributor PRs first, then reorganizing or deduping after merge.
8. Run `python3 scripts/validate_static.py` before every PR.

## Community and contribution

- Open issues and PRs: [openclaw/openclaw](https://github.com/openclaw/openclaw)
- Community chat: [discord.gg/clawd](https://discord.gg/clawd)
- Contribute to this index: see [CONTRIBUTING.md](CONTRIBUTING.md)

When adding resources here:

- prefer canonical sources;
- include dates for volatile claims;
- do not add unsourced superlatives;
- do not hard-code star counts, pricing, or benchmark claims unless they are dated and cited;
- add use cases as patterns with source links, not as fictional stories;
- move outdated but historically useful content to archive pages instead of deleting context silently.

## Archived material

The previous long-form README mixed current resources with old hosting comparisons, pricing tables, security numbers, growth claims, and early ecosystem experiments. It has been archived for historical reference:

- [Legacy README snapshot, 2026-04-27](docs/archive/README-legacy-2026-04-27.md)

Archived material should not be treated as current unless re-verified against official docs, releases, or source code.
