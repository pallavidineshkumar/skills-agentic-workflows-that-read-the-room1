---
name: update-github-info
description: Keep Mona's GitHub Info content current from official GitHub sources.
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
tools:
  edit:
  github:
    toolsets: [repos]
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    max: 1
    draft: true
---

# Update GitHub Info

Keep `site/content/github-info.md` current for Mona's website.

Before making changes:

1. Read `notes/mona-notes.md` with GitHub repository API tools.
2. Read the current `site/content/github-info.md` with GitHub repository API tools.
3. Fetch `https://github.blog/latest/` with the `web-fetch` tool.
4. Fetch `https://github.blog/changelog/` with the `web-fetch` tool.

Use GitHub repository API tools for repository guidance and file reads. Do not use terminal, CLI, or sandboxed commands for GitHub API reads.

Select useful, recent items for developers and update `site/content/github-info.md` with short, practical summaries. Preserve the existing Markdown structure and cite the official source URL for every blog or changelog item. Avoid duplicate entries and do not invent details.

Use the `edit` tool to make the content change. When the update is ready, use the `create-pull-request` safe output to open a draft pull request against `main` for Mona to review. Do not write directly to `main`.
