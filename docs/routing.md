# Routing and escalation

## Picking the starting tier

Ask four questions about the sub-task:

1. Does it touch more than 3 files?
2. Is the spec ambiguous or the cause of a bug unknown?
3. Does it change a contract other code depends on (API, schema, shared types)?
4. Is it security-sensitive?

- All "no": tier 1 (`composer-2.5`).
- Any of 1-3 "yes": tier 2 (`grok-4.7`).
- An architecture decision, or tiers 1 and 2 already failed: tier 3.
- Question 4 does not raise the tier by itself; it raises the review level.

## Escalating

| Attempt | Model |
|---|---|
| 1 | starting tier |
| 2 | same tier, with the real error from attempt 1 |
| 3 | next tier, with both errors |

Pass the failing CI log excerpt or the reviewer's findings verbatim. Keep the same branch and PR so history and context are preserved.

## Examples

- Rename a config key in 2 files, test exists: tier 1.
- Flaky test, cause unknown: tier 2.
- Split a module into a new package boundary: tier 3.
- Change to signing code, 1 file: tier 1 execution, 2-round review from a different model family.
