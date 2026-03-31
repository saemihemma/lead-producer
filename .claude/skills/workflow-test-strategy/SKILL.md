---
name: workflow-test-strategy
description: "Project-level test suite audit, rearchitecture, and strategy. Use when the problem is the test infrastructure itself — not what to test for a single feature."
---
# Test Strategy Workflow

## Purpose
Audit, redesign, or establish test infrastructure at the project level. Owns the macro question: "Is our test suite an asset or a liability, and what do we do about it?"

## Use When
- Test suite is large, slow, flaky, or structurally unsound
- Migrating test frameworks or rearchitecting test infrastructure
- Establishing test strategy from scratch on an existing codebase
- AI agents are generating tests at scale and quality is degrading
- Test maintenance cost is outpacing value

## Do NOT Use When
- Writing tests for a single feature (use `workflow-test-driven-development`)
- Reviewing test coverage for a specific PR (use `role-qa-engineer`)
- Root-cause debugging a test failure (use `workflow-systematic-debugging`)

## Composition
- **role-qa-engineer** (domain owner): test strategy, coverage architecture, risk-based prioritization
- **role-software-architect**: test infrastructure boundaries, framework selection, CI integration shape
- **role-principal-software-engineer**: test code quality, maintainability, redundancy

## Workflow
1. **Audit current state**: suite size, run time, flake rate, coverage shape, framework age, AI-generated test ratio
2. **Identify structural problems**: redundancy, weak assertions, missing layers (unit/integration/e2e imbalance), isolation failures, slow feedback loops
3. **Design target state**: test architecture that protects critical behavior with minimum maintenance cost
4. **Plan migration**: phased approach, what to delete first, what to rewrite, what to keep, framework changes
5. **Execute with TDD discipline**: route implementation slices through `workflow-test-driven-development`

## Default Output
```text
TEST STRATEGY REPORT
====================
Current State: suite size, run time, flake rate, coverage shape, framework
Structural Problems: redundancy, weak layers, isolation failures, maintenance cost
Target State: test architecture, framework, layer balance, CI integration
Migration Plan: phases, deletion targets, rewrite priorities, risk
Verdict: investment justified / defer / partial overhaul
```

## Anti-Drift Rules
- This workflow owns test infrastructure decisions, not feature-level test design.
- Deletion is a valid and often primary recommendation. A smaller, stronger suite beats a large weak one.
- Do not recommend framework migrations without concrete evidence the current framework is the bottleneck.
- Route implementation through TDD workflow. This workflow plans; TDD executes.
