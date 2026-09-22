---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine: copilot
model: gpt-4o-mini
strict: true
tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
---

# Update GitHub Info

Keep the GitHub Info website current with concise, practical updates for developers.

## Instructions

1. Read `notes/mona-notes.md` from the checked-out repository.
2. Use the GitHub repository API tools to read repository guidance and reference files, including the existing `site/content/github-info.md`. Do not use terminal commands, the GitHub CLI, or sandboxed commands to read repository guidance or reference files.
3. Use `web-fetch` to fetch and read https://github.blog/latest/.
4. Use `web-fetch` to fetch and read https://github.blog/changelog/.
5. Use `web-fetch` to fetch and read https://awesome-copilot.github.com/workflows/.
6. Identify useful, recent developer-focused updates from those sources. Keep summaries short and practical, and attribute each update to its source.
7. Use the `edit` tool to update `site/content/github-info.md` while preserving its existing format and unrelated content.
8. Review the resulting change for accuracy, concise wording, source links, and valid Markdown.
9. Use the `create-pull-request` safe output exactly once to open a pull request containing the change for Mona to review. Do not push directly to `main`.
