
# Chichao Beian Agent Instructions

This directory is an Auctra-managed Chinese novel scenario workspace. It is user content and project state, not an implementation subproject. Do not edit `.auctra/**` structured assets by hand; use Auctra commands for project, scenario, gate, chapter, material, review, and export operations.

Active runtime skills are generated from `.skills/profiles/targets/data/chichao-beian.txt` into both `.agents/skills/` and `.claude/skills/`.

<!-- runtime-skills:start -->
- `auctra-i18n-workspace-router`
- `auctra-novel-optimization-loop`
- `auctra-novel-review-orchestrator`
- `chinese-novel-chapter-reviewer`
- `chinese-novel-chapter-writer`
- `chinese-novel-character-architect`
- `chinese-novel-context-pack-builder`
- `chinese-novel-continuity-editor`
- `chinese-novel-dialogue-editor`
- `chinese-novel-draft-comparator`
- `chinese-novel-adaptation-architect`
- `chinese-novel-analysis-decomposer`
- `chinese-novel-brief-architect`
- `chinese-novel-content-spinoff-architect`
- `chinese-novel-genre-contract-strategist`
- `chinese-novel-hook-pacing-editor`
- `chinese-novel-length-form-architect`
- `chinese-novel-orchestrator`
- `chinese-novel-outline-architect`
- `chinese-novel-project-bible-keeper`
- `chinese-novel-reader-retention-editor`
- `chinese-novel-revision-producer`
- `chinese-novel-scene-card-writer`
- `chinese-novel-state-ledger-updater`
- `chinese-novel-serial-operations-editor`
- `chinese-novel-style-polisher`
- `chinese-novel-volume-arc-planner`
- `creative-writing-router`
- `yeisme-auctra-cli-runtime`
<!-- runtime-skills:end -->


<!-- skillctl:scenario-routing:start -->
# Auctra Scenario Routing

Scenario: auctra-scenario-novel
Skill set: creative-writing-chinese-novel

For Chinese novel planning, drafting, continuation, review, continuity checks, reader promise checks, or chapter polishing, load `chinese-novel-orchestrator` first and then route to the relevant `chinese-novel-*` specialist skill. Do not draft or revise novel chapters before checking Auctra scenario gates.

Routing order for this project:

1. `creative-writing-router` identifies phase and artifact; `auctra-i18n-workspace-router` owns localized paths and `.auctra/**` boundaries.
2. `chinese-novel-context-pack-builder` prepares the minimum project context before any write or review.
3. Planning uses `chinese-novel-genre-contract-strategist`, `chinese-novel-project-bible-keeper`, `chinese-novel-outline-architect`, `chinese-novel-volume-arc-planner`, `chinese-novel-character-architect`, and `chinese-novel-scene-card-writer` as needed.
4. Writing uses `chinese-novel-chapter-writer`; review enters through `auctra-novel-review-orchestrator` and then the smallest reviewer/editor skill.
5. Accepted changes feed `chinese-novel-state-ledger-updater`; repeated defects feed `auctra-novel-optimization-loop` before the next revision.

The following skills are intentionally outside this workspace's active scenario profile: `auctra-chinese-project-starter` and `creative-writing-orchestrator`. The scenario-required specialist skills remain installed so `auctra gate check` can enforce the full contract, but they should only be loaded when the task artifact calls for them.

Required command checks:

```bash
auctra scenario doctor --json
auctra gate check --before chapter_write --json
```
<!-- skillctl:scenario-routing:end -->
