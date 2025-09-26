# Readme

## Prerequisites

- Node.js 18 or newer
- login into:
  - a Claude account <https://claude.ai/>
  - or Claude Console account here: <https://console.anthropic.com/>
- VSCode
  - Claude Official Extension for VSCode: <https://marketplace.visualstudio.com/items?itemName=anthropic.claude-code>
    then:

```sh
# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Navigate to your project
cd your-awesome-project

# Start coding with Claude
claude
# You'll be prompted to log in on first use
# Follow the setup and choose between
# 1. Claude account with subscription
#    Pro, Max, Team, or Enterprise
# or
# 2. Anthropic Console account
#    API usage billing
# then set the API key
```

Use `/status` inside Claude to confirm which auth is active. If you ever need to switch, `/logout` and re-set the variable. (Keep in mind: some builds nudge you to login if a cached session exists; clearing `~/.claude*` resets it.)

```ai
/status
```

Enable IDE goodies

Inside Claude, run:

```sh
/config
```

## `@file` references

To insert @file references into the prompt: `⌥/Alt+Cmd+K`

## Bootstrap project memory (`CLAUDE.md`)

Create a project memory file (helps Claude “think with” your rules and scripts):

```sh
/init
```

This writes `./CLAUDE.md` (or `./.claude/CLAUDE.md`). You can later include files with `@path/to/file` and manage memories with `/memory`.

## Commands

Create this command `.claude/commands/commit.md`:

```md
# Commit Changes

You are tasked with creating git commits for the changes made during this session.

## Process:

1. **Think about what changed:**

   - Review the conversation history and understand what was accomplished
   - Run `git status` to see current changes
   - Run `git diff` to understand the modifications
   - Consider whether changes should be one commit or multiple logical commits

2. **Plan your commit(s):**

   - Identify which files belong together
   - Draft clear, descriptive commit messages
   - Use imperative mood in commit messages
   - Focus on why the changes were made, not just what

3. **Present your plan to the user:**

   - List the files you plan to add for each commit
   - Show the commit message(s) you'll use
   - Ask: "I plan to create [N] commit(s) with these changes. Shall I proceed?"

4. **Execute upon confirmation:**
   - Use `git add` with specific files (never use `-A` or `.`)
   - Create commits with your planned messages
   - Show the result with `git log --oneline -n [number]`

## Important:

- **NEVER add co-author information or Claude attribution**
- Commits should be authored solely by the user
- Do not include any "Generated with Claude" messages
- Do not add "Co-Authored-By" lines
- Write commit messages as if the user wrote them

## Remember:

- You have the full context of what was done in this session
- Group related changes together
- Keep commits focused and atomic when possible
- The user trusts your judgment - they asked you to commit
```

Now relaunch Claude in this project and list available commands with `/help`
