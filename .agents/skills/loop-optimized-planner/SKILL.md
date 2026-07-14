---
name: loop-optimized-planner
description: Design and run minimal, durable goal loops for work spanning phases, iterations, hours, or context resets. Use when any coding assistant needs a compact phased plan, a self-feeding execution cycle, persistent loop memory, bounded delegation, or protection against drift and stalled long-running work.
---

# Loop Optimized Planner

Build the smallest loop that can stay aligned, recover, and finish.

## Adapt the guidance

- Explicit user instructions override every default.
- Start with the smallest loop that can finish; add structure only after a real need appears.
- Use budgets and cadence to drive decisions; never invent universal counts.
- Enforce hard invariants with tools, state, permissions, or checks—not prompt text alone.

## Clarify the goal and shape the plan

- Clarify every material dimension: outcome, quality, speed, scope, risk, evidence, budget, and decision authority.
- Add non-goals, reversibility, uncertainty, and stop boundaries when they change how the work should run.
- Match effort and rigor to the user's expectation: quick result, high assurance, or rapid exploration.
- Separate non-negotiable intent from adjustable tactics; ask before inventing a hard requirement.
- Use the fewest phases that expose real decisions; give each an observable done state.
- Keep only the current iteration concrete; revise the plan when evidence shows it is wrong.
- For long-running work, add milestone triggers that reread this skill before goal realignment.
- Include only concerns justified by the request, environment, evidence, or material risk.
- Never fill unknowns with generic phases, gates, roles, policies, or other ceremony.

## Prefer clear role ownership

- Prefer one orchestrator using the strongest reliable model available.
- The orchestrator owns goals, strategy, integration, verification, memory, and closure.
- Give workers bounded, checkable execution tasks; keep strategic judgment with the orchestrator.
- State each worker's outcome, scope, inputs, evidence, stop condition, and prohibited decisions.
- Verify every return against primary evidence; split or reclaim vague or failed tasks.
- Use a distinct strong advisor to challenge framing, stagnation, pivots, and closure.
- Treat advisor output as a hypothesis; the orchestrator retains decision authority.
- Omit roles when a simpler topology is enough.
- Parallelize only independent work the orchestrator can review.
- For exploration, give workers different questions; duplicate assignments add no useful entropy.

## Run ordinary iterations

- **Orient:** reconcile the goal, phase, compact state, and actual environment.
- **Choose:** select the smallest step with the highest value.
- **Predict:** name the expected evidence and strongest falsifier.
- **Act:** execute directly or issue one bounded handoff.
- **Observe:** inspect authoritative environmental evidence.
- **Decide:** keep, repair, revert, split, pivot, defer, wait, escalate, or stop.
- **Checkpoint:** preserve a clean, recoverable state and record what matters later.
- Work in small steps so each change can be evaluated; avoid giant one-shot changes with unclear impact.
- Revert, delete, or pivot when evidence shows the current direction is wrong.
- Never wait blindly; use a timeout or proactive progress monitoring.
- Default to 10 minutes, then recalibrate the timeout to the command's expected runtime.
- A short timeout can kill healthy work; timing out does not prove the command was stuck.
- After each checkpoint, continue normally or run milestone realignment when triggered.

## Run a Milestone realignment

Run this occasional step-back when:

- A meaningful phase or milestone finishes.
- Work or context becomes hard to hold in overview.
- Progress stalls or repeats without new evidence.
- Scope, assumptions, constraints, or important evidence changes.

Do not run it after every small step or on an arbitrary timer.

At the checkpoint:

- Reread this skill, the original request, and compact memory from the top.
- Restate the non-negotiable goal; discard stale assumptions and bad intermediate goals.
- Inspect the cumulative work and evidence.
- Compare the work with the user's goal; continue, restore, remove, or pivot.
- Revise adjustable goals and phases when evidence supports it.
- Ask before changing user-owned intent unless the user delegated that authority.
- Verify the integrated state; compact memory and context; then resume.

Use `reread skill -> restate goal -> compare -> realign -> verify -> compact -> resume`.

## Milestone realignment reread

- **False priority or nerd-sniping:** Was this asked for, and is it worth the time?
- **Local optimization:** Are small gains hiding that the direction should be replaced?
- **Strategy fixation:** Have we tried a materially different angle or fresh evidence?
- **Blind waiting:** Is every slow task bounded or actively monitored?
- **Timeout fit:** Is the bound realistic for this command?
- **Repeated stalls:** Are retries producing new evidence?
- **Scope drift:** Did an adjacent issue, tool, or cleanup become the mission?
- **Weak proof:** Is evidence getting stronger, or repeating the same shallow check?
- **Stale evidence:** Did later changes invalidate earlier verification?
- **Context drift:** Can the orchestrator state the goal, truth, decisions, and next action immediately?
- **Excess work:** Can the orchestrator review and integrate everything in flight?
- **Late closure:** Is optional improvement stealing time from integration and verification?
- **Wrong pace:** Would a timely good result better satisfy the user?

When value flattens, preserve the best verified state and finish, pivot, or ask.

## Close honestly

- Reserve time for integration, verification, explanation, and cleanup.
- Claim completion only from fresh evidence on the final state.
- For delivery, report the result, verification, material decisions, and known limits.
- For exploration, report the question, tested alternatives, positive and negative evidence, and current decision.
- If incomplete, report the exact state, retained evidence, and smallest resume action.

## Keep durable memory clean

- Keep one compact current state: goal, style, phase, last verified state, blocker or job, and next action.
- Store it in one task-local log so a fresh orchestrator can resume without replaying history.
- Log only important outcomes, evidence, decisions, failures, pivots, lessons, and resume points.
- Checkpoint before destructive pivots; record why the direction was rejected.
- Remove rejected code from the active workspace; preserve it through history and referenced artifacts.
- Update memory after milestones, consequential failures, long waits, and before context loss.
- Record execution truth, not narration or plan-edit history; link evidence instead of copying it.
- Let the observed environment outrank memory whenever they disagree.

## Core insight

The agent loop is not a chain. It is a cycle.

```text
GOAL -> PLAN -> ACT -> OBSERVE -> DECIDE -> CHECKPOINT
          ^                                  |
          |                                  +-- ordinary -> next iteration
          |                                  |
          +-- REALIGN GOALS <- REREAD SKILL -+-- milestone, stall, or drift
                                             |
                                             +-- goal met -> verify -> final output
```
