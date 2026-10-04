# Set up Reading Scout

Install or reuse the skill, ask for missing choices, check access, and save the profile. Stop after setup unless the user also asked for a scan.

## Install

If Reading Scout is available through an installed plugin or local skill, read its `SKILL.md` and continue to **Ask for choices**. Use the installed copy; do not clone or copy it into `~/.agents/skills/`.

Otherwise register the repo marketplace with `codex plugin marketplace add yuhan/reading-scout` using Codex CLI. Help the user install **Reading Scout** from that source in Plugins. Ask them to start a new chat and say “Set up Reading Scout.” Continue setup once the installed skill is available. If marketplace setup is unavailable, explain the gap and offer direct skill installation.

For direct skill installation, clone `https://github.com/yuhan/reading-scout.git` or use a local checkout supplied by the user. Read `skills/reading-scout/SKILL.md`, then copy the whole skill folder into `~/.agents/skills/reading-scout/`, including `references/` and `assets/`. Reuse an existing installation without overwriting it. See [Codex local skills](https://developers.openai.com/codex/skills).

Codex detects new skills automatically. If it does not appear, ask the user to restart Codex and say “Continue Reading Scout setup.” Report file-access problems rather than claiming installation succeeded.

## Ask for choices

Check existing state and available tools. Reuse prior answers and ask only for what is missing:

- **Interests and workspace:** What research questions should the scout follow, and where should its state live? Offer the current workspace unless it is the skill source or install folder. Watch topics and exclusions can wait.
- **Discovery:** Offer X research posts or web search only.
- **Reading queue:** Offer Notion, a Space Page, or no queue. With no queue, suggestions and feedback stay local; there is no separate reading-status tracker.

X and a queue are optional. Use the chosen queue; do not copy entries to another destination unless asked.

## Check access

Use the host's tools and relevant integration skills. Reuse working connections and handle the steps you can; explain any sign-in or permissions the user must finish.

**Web:** Check that search and original-source access are available.

**X:** Check research-post search and direct-post lookup with a small read-only test. If no connection exists, help the user choose a supported integration or MCP provider using its current official instructions. Explain credentials and costs before setup; keep secrets in the provider's secure configuration. If access is blocked, mark X pending and offer web search.

**Notion:** Connect Notion if needed, then ask for the reading database and inspect its schema and entries. If none exists, offer to create a Reading database in the user's chosen parent Page, with title, URL, and status fields. Create it only when requested and verify it. Help the user grant access if needed.

**Space:** Check that Page tools are available, then read the chosen Space or reading Page. Reuse an existing list, or offer to create a Reading Page in the chosen Space. Create it only when requested and verify it. Use a list with title, URL, and reading status.

Record the chosen destination. Do not add sample readings or change sharing during setup. Report missing access; skipped connections are not failures.

## Save and finish

Create `.reading-scout/` in the chosen workspace, outside the skill source and install folders. Copy the [profile](../assets/profile.md) and [feedback](../assets/feedback.csv) templates only when missing. Preserve existing state.

Fill the profile with the user's interests, chosen sources, queue destination, and any pending connections. Record a skipped X connection so later scans respect the choice. Feedback guides picks; it does not rewrite the user's topics.

Add `.reading-scout/` to the working repository's ignore file when needed. Without file access, explain that context can be used in the chat but cannot be saved.

Finish with the state location, interests, and connections that are ready, skipped, or pending. Tell the user to open that workspace for later scans and say:

> Run Reading Scout. Find research worth my attention.

Save readings or create a schedule only when asked.
