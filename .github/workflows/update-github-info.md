---
name: update-github-info
description: Keep Mona's GitHub Info content current using official GitHub Blog, Changelog, and Awesome Copilot workflows updates.
on:
  schedule:
    - cron: "0 14 * * *"
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
---

# Update GitHub Info

Read `notes/mona-notes.md` and the current `site/content/github-info.md` before drafting any changes.

Use the web-fetch tool to fetch all three sources:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/ (Awesome Copilot workflows)

Use only verifiable, relevant information from those sources. Update only `site/content/github-info.md`, preserving Mona's practical editorial angle and the existing content structure where it still fits. Keep summaries short and useful to developers, and cite the originating Blog, Changelog, or Awesome Copilot URL for every new or changed claim. Do not invent details or remove still-accurate themes without evidence.

If there is a meaningful update, use the edit tool to change the file and request one pull request through the configured safe output for Mona to review. The pull request should briefly summarize the content changes and link to the source pages. Do not push changes directly to a branch or modify any other files. If no meaningful, source-backed update is available, leave the file unchanged and do not open an empty pull request.