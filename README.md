# Voxmind Documentation

This repository contains the source files for the Voxmind developer documentation, published at `docs.voxmind.ai` via Mintlify.

## Repository structure

```
voxmind-docs/
├── mint.json                          ← Mintlify config (navigation, branding, colours)
├── logo/                              ← Brand assets (voxmind-white.png, voxmind-dark.png)
├── images/                            ← Hero images and diagrams
├── favicon.png
│
├── getting-started/
│   ├── introduction.mdx               ← Landing page for docs
│   ├── quickstart.mdx                 ← 5-minute enroll/verify walkthrough
│   ├── authentication.mdx             ← Token management guide
│   └── environments.mdx               ← Sandbox vs production
│
├── guides/
│   ├── how-voice-biometrics-works.mdx ← Core concept: phoneme-level analysis
│   ├── enrollment-best-practices.mdx  ← Audio quality, UX patterns
│   ├── deepfake-detection.mdx         ← Deepfake detection guide (TODO)
│   ├── language-support.mdx           ← Supported languages and codes
│   ├── webhooks.mdx                   ← Async result handling
│   ├── contact-center-integration.mdx ← Vertical guide (TODO)
│   ├── web-app-integration.mdx        ← Vertical guide (TODO)
│   ├── mobile-integration.mdx         ← Vertical guide (TODO)
│   └── filtering-sorting-pagination.mdx
│
├── api-reference/
│   ├── voice/
│   │   ├── enroll.mdx                 ← POST enrollments
│   │   └── verify.mdx                 ← POST verifications
│   ├── tokens/                        ← API token CRUD (TODO)
│   ├── organisation/                  ← Org + settings endpoints (TODO)
│   ├── users/                         ← User management (TODO)
│   ├── billing/                       ← Plans, subscriptions, invoices (TODO)
│   ├── devices/                       ← Device management (TODO)
│   └── predefined-texts/              ← Text management (TODO)
│
└── resources/
    ├── error-codes.mdx
    ├── rate-limits.mdx
    ├── security.mdx                   ← Security overview (TODO)
    └── changelog.mdx                  ← (TODO)
```

## Setup instructions

### 1. Install the Mintlify CLI

```bash
npm install -g mintlify
```

### 2. Run locally

```bash
cd voxmind-docs
mintlify dev
```

The docs will be available at `http://localhost:3000`.

### 3. Connect to Mintlify dashboard

1. Sign up or log in at [mintlify.com](https://mintlify.com)
2. Create a new project and connect this GitHub repository
3. In the Mintlify dashboard, set your custom domain to `docs.voxmind.ai`
4. Add the CNAME record in AWS Route 53: `docs.voxmind.ai` → Mintlify's provided CNAME target

### 4. Add logo and brand assets

Add the following files to the `logo/` directory:
- `voxmind-white.png` — Logo for dark mode backgrounds (white/light version)
- `voxmind-dark.png` — Logo for light mode backgrounds (dark/blue version)
- `favicon.png` — 32×32px favicon

### 5. Environment variables in Mintlify

No env vars are required. The `mint.json` file contains all configuration including the `api.baseUrl` for the interactive API playground.

## Writing conventions

All content is written in `.mdx` format (Markdown + React components). Use Mintlify's built-in components rather than raw HTML: `<Note>`, `<Warning>`, `<Info>`, `<Tip>`, `<Card>`, `<CardGroup>`, `<CodeGroup>`, `<RequestExample>`, `<ResponseExample>`, `<ParamField>`, `<ResponseField>`.

Write in plain, direct language. Developers are busy — every sentence should earn its place. Lead with what the thing does, then explain how, then show an example. Never bury the most important information below the fold.

## Deployment

Mintlify auto-deploys on every push to the `main` branch. No CI/CD configuration required — just push to GitHub and Mintlify handles the rest, typically deploying within 60 seconds.
