# simorgh-articles

Technology articles for the Simorgh AI website. Push a new article directory and it automatically appears on the site with AI-generated summaries.

## How to add a new article

1. Create a directory under `articles/` with a slug name (e.g., `articles/my-new-topic/`)
2. Add these files inside it:

```
articles/my-new-topic/
├── en.md          # English article (Markdown)
├── fa.md          # Persian article (Markdown)
└── meta.json      # Metadata (title, author, date, tags)
```

3. `meta.json` format:

```json
{
  "title_en": "My New Topic",
  "title_fa": "موضوع جدید من",
  "author": "Author Name",
  "date": "2026-02-26",
  "tags": ["AI", "Technology"]
}
```

4. Push to `main` branch. The GitHub Actions workflow will:
   - Generate EN and FA summaries using OpenAI API
   - Build `articles.json` manifest
   - Deploy everything to the VPS via rsync/SSH
   - Restart the landing site container

## Required GitHub Secrets

| Secret | Description |
|--------|-------------|
| `OPENAI_API_KEY` | OpenAI API key for generating article summaries |
| `VPS_SSH_PRIVATE_KEY` | SSH private key for accessing the VPS |
| `VPS_SSH_USER` | SSH username on VPS (e.g., `root`) |
