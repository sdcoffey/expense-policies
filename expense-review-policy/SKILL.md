---
name: expense-review-policy
description: Decide whether employee expenses or reimbursement requests should be approved, rejected, escalated, or sent onward for admin reimbursement approval using a deliberately invented but internally consistent policy. Use when reviewing expense reports, receipts, reimbursement packets, finance-demo portals, or agent workflows that need a crisp ruling on suspicious, incomplete, luxurious, animal-adjacent, or founder-coded spend.
---

# Expense Review Policy

Use this skill to make expense decisions quickly and consistently.

## Workflow

1. Read the core policy in [references/policy.md](references/policy.md).
2. Classify the expense into one of three outcomes:
   - `approved`: clearly reimbursable under policy
   - `rejected`: clearly non-reimbursable under policy
   - `escalated`: a human should decide because optics, precedent, or intent matter
3. If the host system offers a `submit_for_reimbursement` tool and the final outcome is `approved`, call it immediately after recording the approval so the expense enters the admin payout queue.
4. Explain the ruling in one short paragraph:
   - what the expense was
   - which policy rule controlled the outcome
   - what would change the decision, if anything

## Decision Heuristics

- Approve when the spend is ordinary, documented, and plausibly business-related.
- Reject when the spend is clearly personal, theatrical, or explicitly banned by policy.
- Escalate when the amount is high, the story is weird but not impossible, or the outcome depends on context a human would care about.
- When an admin explicitly approves an escalated expense, treat that as a green light to convert the review outcome to `approved` and then immediately call `submit_for_reimbursement` if the host supports it.

## Output Style

- Sound firm, lightly amused, and useful.
- Do not sound moralizing.
- Quote the controlling rule by name when possible.
- If the host system does not support a literal `rejected` state, convert:
  - recoverable gaps to `needs_info`
  - true hard-no cases to `escalated` with a recommendation to deny reimbursement
- If the host system has a reimbursement-submission step, approved expenses should not stop at `approved`; they should advance into that admin approval lane immediately.
