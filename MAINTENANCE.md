# Repository Maintenance Protocol

To ensure consistency and quality, the following steps MUST be performed for **every single change** involving skills or documentation.

## 1. Skill Creation & Modification

- [ ] **Check Duplicates**: Before adding a skill, check `skills_index.json` or `ls skills/` to ensure it doesn't exist.
- [ ] **Folder Structure**: Each skill must have its own folder in `skills/<skill-name>`.
- [ ] **SKILL.md**: Every skill directory MUST contain a `SKILL.md` file with valid frontmatter:
  ```markdown
  ---
  name: Skill Name
  description: Brief description.
  ---
  ```

## 2. Validation & Indexing (CRITICAL)

Running the scripts is **MANDATORY** after any change to `skills/`.

- [ ] **Validate Skills**: Run the validation script to check for formatting errors.
  ```bash
  python3 scripts/validate_skills.py
  ```
- [ ] **Generate Index**: Update `skills_index.json`. This is the source of truth for the agent.
  ```bash
  python3 scripts/generate_index.py
  ```

## 3. Documentation Updates

The `README.md` does not auto-update. You must manually sync it with the index.

- [ ] **Update Skill Count**: Check the output of `generate_index.py` (e.g., "Generated index with 131 skills") and update the badge/text in `README.md`.
  - Line ~3: `> **The Ultimate Collection of [NUMBER]+ Agentic Skills...`
  - Line ~9: `...library of **[NUMBER] high-performance skills**...`
  - Line ~39: `## Full Skill Registry ([NUMBER]/[NUMBER])`
- [ ] **Update Registry Table**: If new skills were added, add them to the alphabetical table in `README.md`.
- [ ] **Update Categories**: If the skill fits a specific category (e.g., Security, Design), update the "Features & Categories" table.

## 4. Git Operations

- [ ] **Check Status**: `git status` to see what changed.
- [ ] **Add All Files**: Ensure new skill folders are added (`git add skills/`).
- [ ] **Commit**: Use a descriptive Conventional Commit message (e.g., `feat: add new security skills`, `docs: update readme count`).
- [ ] **Push**: `git push` to origin. **NEVER FORGET THIS.**

## 5. Agent Artifacts (Internal)

- [ ] **Walkthrough**: Update `walkthrough.md` in the brain/artifact directory to reflect the session's achievements.
