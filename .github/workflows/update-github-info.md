---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
network:
  allowed:
    - github.blog
    - github.com
tools:
  github:
    toolsets: [repos]
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    allowed-files:
      - site/content/github-info.md
    max: 1
---

# Update Mona's GitHub information

Keep Mona's GitHub Info website current with useful, official GitHub updates.

1. Use GitHub repository API tools to read `notes/mona-notes.md` and the current
   `site/content/github-info.md`. Do not use terminal, CLI, or sandboxed commands
   to read repository guidance or reference files.
2. Use `web-fetch` to read `https://github.blog/latest/` and
   `https://github.blog/changelog/`.
3. Select a small set of recent, practical updates that help developers learn GitHub
   faster. Follow Mona's editorial notes, keep summaries short, and include the
   official source URL for every Blog or Changelog item.
4. Update only `site/content/github-info.md`. Preserve its existing Markdown
   structure and retain still-relevant material.
5. When the content changes, use the `create-pull-request` safe output to open a
   pull request for Mona to review. Summarize the selected updates and link their
   sources in the pull request body. If no worthwhile update is available, do not
   open a pull request.