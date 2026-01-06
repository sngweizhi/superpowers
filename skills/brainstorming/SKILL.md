---
name: brainstorming
description: "Use when designing features, components, or modifications. Explores codebase context and user intent before implementation."
---

# Brainstorming Ideas Into Designs

## Overview

Help turn ideas into fully formed designs and specs through natural collaborative dialogue.

**Before asking ANY questions**, research the codebase first using parallel subagents to understand existing patterns, architecture, and constraints. Then ask targeted questions informed by what you learned.

## The Process

### Step 1: Codebase Research (MANDATORY - Do First)

Fire parallel explore agents BEFORE engaging with the user:

```typescript
// Launch these in parallel immediately
background_task(agent="explore", prompt="Find similar features/components to [topic]. Look for patterns, architecture, data flow.")
background_task(agent="explore", prompt="Find configuration, types, and interfaces related to [topic].")
background_task(agent="explore", prompt="Find tests and error handling patterns for similar features.")
```

Wait for results before proceeding. This research informs your questions and proposals.

### Step 2: Understanding the Idea

With codebase context in hand:
- Ask questions one at a time to refine the idea
- Reference existing patterns you found: "I see you use X pattern for similar features..."
- Prefer multiple choice questions when possible
- Focus on understanding: purpose, constraints, success criteria

### Step 3: Exploring Approaches

- Propose 2-3 different approaches with trade-offs
- Ground proposals in existing codebase patterns discovered in Step 1
- Present options conversationally with your recommendation and reasoning
- Lead with your recommended option and explain why

### Step 4: Presenting the Design

- Once you believe you understand what you're building, present the design
- Break it into sections of 200-300 words
- Ask after each section whether it looks right so far
- Cover: architecture, components, data flow, error handling, testing
- Be ready to go back and clarify if something doesn't make sense

## After the Design

**Documentation:**
- Write the validated design to `docs/plans/YYYY-MM-DD-<topic>-design.md`
- Use elements-of-style:writing-clearly-and-concisely skill if available
- Commit the design document to git

**Implementation (if continuing):**
- Ask: "Ready to set up for implementation?"
- Use superpowers:using-git-worktrees to create isolated workspace
- Use superpowers:writing-plans to create detailed implementation plan

## Key Principles

- **Research first, ask second** - Never ask questions you could answer from the codebase
- **One question at a time** - Don't overwhelm with multiple questions
- **Ground in reality** - Reference existing patterns when proposing solutions
- **YAGNI ruthlessly** - Remove unnecessary features from all designs
- **Explore alternatives** - Always propose 2-3 approaches before settling
- **Incremental validation** - Present design in sections, validate each
