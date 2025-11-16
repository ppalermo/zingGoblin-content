# ZingGoblin Content Seeds

This repository contains manual content seeds for the ZingGoblin news roaster.

## Adding New Content

### Quick Add via GitHub Web UI (Recommended!)

1. Go to https://github.com/ppalermo/zingGoblin-content
2. Navigate to `seeds/` directory
3. Click "Add file" → "Create new file"
4. Name: `seeds/YYYY-MM-DD-descriptive-name.json`
5. Copy template from `templates/seed-template.json`
6. Fill in your content details
7. Commit directly to main branch

### Add via GitHub Mobile App

Perfect for adding content on-the-go!

1. Open GitHub app
2. Navigate to this repository
3. Browse to `seeds/` folder
4. Tap "+" → "Create new file"
5. Add your content using the template
6. Commit

### Add Locally

```bash
cd ~/zingGoblin-content
nano seeds/breaking-news-$(date +%Y-%m-%d).json
# Add your content
git add seeds/
git commit -m "Add breaking news content"
git push
```

## File Naming Convention

Use descriptive names with dates:
- `seeds/2024-01-15-nick-fuentes-rant.json`
- `seeds/2024-01-16-pvd-controversy.yaml`
- `seeds/breaking-news-2024-01-17.json`

## Content Templates

### Minimal Example (JSON)
```json
{
  "source_type": "youtube",
  "source_id": "dQw4w9WgXcQ",
  "source_url": "https://youtube.com/watch?v=dQw4w9WgXcQ",
  "title": "Controversial video title",
  "priority": "high"
}
```

### Full Example (JSON)
```json
{
  "source_type": "x",
  "source_id": "1234567890",
  "source_url": "https://twitter.com/username/status/1234567890",
  "source_author": "Nick Fuentes",
  "source_author_handle": "@NickJFuentes",
  "title": "Controversial tweet about immigration",
  "description": "Hot take on recent immigration policy",
  "transcript": "Full text of the tweet goes here...",
  "priority": "high",
  "metadata": {
    "notes": "This is going viral, needs immediate roast",
    "tags": ["politics", "immigration", "controversy"],
    "urgency": "breaking"
  }
}
```

### YAML Example
```yaml
source_type: youtube
source_id: dQw4w9WgXcQ
source_url: https://youtube.com/watch?v=dQw4w9WgXcQ
title: Controversial video title
description: Brief description
priority: high

metadata:
  notes: Important context
  tags:
    - breaking
    - scandal
```

## Required Fields

- `source_type`: youtube, x, tiktok, or manual
- `source_id`: Unique identifier (can be extracted from URL)
- `title`: Title or brief description
- `priority`: low, medium, or high

## Optional Fields

- `source_url`: Full URL to the content
- `description`: Detailed description
- `transcript`: Full text content/transcript
- `source_author`: Author/creator name
- `source_author_handle`: Social media handle
- `metadata`: Any additional information (free-form)

## Priority Levels

- **high**: Breaking news, viral content, immediate attention
- **medium**: Normal content, process in order
- **low**: Backlog, process when nothing else available

## Syncing with ZingGoblin

After adding content to this repository:

```bash
# In your ZingGoblin app
docker-compose run --rm news-jester sync-content --auto-import

# Then generate scripts
docker-compose run --rm news-jester generate --spice 7
```

## Repository Structure

```
zingGoblin-content/
├── README.md (this file)
├── seeds/
│   ├── 2024-01-15-example.json
│   ├── 2024-01-16-another.yaml
│   └── ...
└── templates/
    ├── seed-template.json
    └── seed-template.yaml
```

## Tips

1. **Use GitHub web UI** - Fastest way to add content
2. **Add dates to filenames** - Easy to track and organize
3. **Use high priority sparingly** - Reserve for truly urgent content
4. **Add notes in metadata** - Remember why content matters
5. **Both JSON and YAML work** - Use whichever you prefer

## Troubleshooting

### Authentication Issues

```bash
# Test GitHub SSH
ssh -T git@github.com

# Should see: "Hi username! You've successfully authenticated"
```

### Invalid JSON/YAML

- Use https://jsonlint.com to validate JSON
- Use https://yamlchecker.com to validate YAML
- Ensure all required fields are present
- Check for trailing commas in JSON

## Questions?

See the main ZingGoblin repository for full documentation:
https://github.com/ppalermo/ZingGoblin
