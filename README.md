# Automated MEL Reporting System

An end-to-end automation pipeline that turns raw training data into AI-generated Monitoring, Evaluation and Learning (MEL) reports — built for **VINAAA-I** (Voices in Nigeria Adolescents and Advocacy Initiative).

## What It Does

Training programs generate a lot of data — attendance, pre-test scores, post-test scores — that usually sits in spreadsheets and never becomes a real report. This system closes that gap automatically:

1. **Attendance & Pre-Test Sync** — Participant attendance and pre-test scores are captured and synced into Airtable.
2. **Training Delivery** — Facilitators run the training session.
3. **Post-Test Sync** — Post-test scores are captured and synced the same way.
4. **AI-Generated Report** — An AI agent compares pre/post scores, summarizes training impact, and evaluates outcomes against VINAAA-I's strategic plan (retrieved via a Pinecone vector store — no raw strategic plan document is stored in this repo).
5. **Delivery** — The final report is generated as a Google Doc, exported to PDF, and delivered via Gmail to the relevant stakeholders.

## Why It Matters

MEL reporting is usually manual, slow, and inconsistent — someone has to pull numbers, write a narrative, and format a document by hand. This system removes that bottleneck: once attendance and scores are logged, the report writes and sends itself, consistently, every time.

## Architecture

Airtable (Attendance + Pre-Test)
        -> n8n Orchestration
        -> Airtable (Post-Test Sync)
        -> AI Agent (Groq) + Pinecone (Strategic Plan Alignment)
        -> Google Docs (Report Template Fill)
        -> Google Drive (Export to PDF)
        -> Gmail (Delivery)

## Tech Stack

- **n8n** — workflow orchestration (self-hosted)
- **Airtable** — training data storage (attendance, pre-test, post-test)
- **Groq (Llama 3.3 70B)** — AI report generation
- **Pinecone** — vector store for strategic plan alignment
- **Google Docs / Drive** — report templating and PDF export
- **Gmail** — automated report delivery

## Data & Privacy

This repository contains **workflow logic only**. No real participant data, attendance records, test scores, or VINAAA-I's actual strategic plan document are included or committed at any point.

## Status

Actively in development. Core pre-test sync is working; post-test sync and report delivery are being finalized.
