
# Agentic AI Assistance for Content Creators

An end-to-end, AI-driven content automation system for research, video generation, and multi-platform publishing, built on n8n.

**Author:** N. Bhargava Teja (ME22B2006)
**Supervisor:** Dr. M. Arul Kumar, Department of Mechanical Engineering
**Institute:** IIITDM Kancheepuram, Chennai
**Degree:** B.Tech project, May 2026

## Overview

Content creation involves research, script writing, recording, editing, and publishing. This project automates the whole pipeline with an agentic workflow, while keeping a human in control through approval loops before anything is generated or published.

## Pipeline

1. **Trigger:** the user sends a command through a WhatsApp (Green API) or Telegram (BotFather) bot, received by an n8n webhook.
2. **Retrieval:** SERP API and Tavily fetch the latest news (title, URL, snippet).
3. **Storage:** cleaned results are stored in Google Sheets, which acts as the retrieval memory.
4. **RAG script generation:** an LLM writes a script grounded only in the retrieved articles.
5. **Human approval:** the user approves, rejects, or gives feedback, and the script is regenerated until accepted.
6. **Voice cloning:** ElevenLabs narrates the script in the client's cloned voice.
7. **Avatar generation:** HeyGen creates a lip-synced upper-body avatar video.
8. **Background generation:** AI-generated images or loops matched to the script.
9. **Video composition:** FFmpeg merges avatar, background, intro, outro, and transitions.
10. **Video approval loop:** the user reviews the final video.
11. **Metadata and publishing:** SEO titles, descriptions, and hashtags are generated, then the video is uploaded to YouTube, Instagram, LinkedIn, Facebook, and Telegram.
12. **Logging and alerts:** every step is logged to Google Sheets, and errors trigger alerts via WhatsApp, Telegram, and email.

## Architecture layers

Interaction, Orchestration (n8n), Retrieval, Storage, Intelligence (LLM + RAG), Validation (human-in-the-loop), Media, Social Publishing, Monitoring.

## Tech stack

| Component | Tool |
|---|---|
| Orchestration | n8n |
| Messaging | WhatsApp (Green API), Telegram Bot API |
| Retrieval | SERP API, Tavily, Perplexity |
| LLM | Azure OpenAI, Ollama |
| Voice | ElevenLabs |
| Avatar | HeyGen |
| Video editing | FFmpeg |
| Logging | Google Sheets |

## Results

- Production time per video reduced from about 4 hours to 10-15 minutes (about 94% time saved).
- Estimated cost of about $0.25 per minute of video (HeyGen about $0.00167/sec, ElevenLabs about $0.001/sec, other components open-source or free tier).

## Future work

A complete web and mobile application to replace the WhatsApp/Telegram interface, and adaptation to other domains such as marketing, education, healthcare, and corporate communication.

## Documents

- [Project report](docs/project-report.pdf)
- [End-semester presentation](docs/end-semester-presentation.pdf)
- [Poster](docs/poster.pdf)

## Reference

P. Lewis et al., "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks," NeurIPS, 2020.
