# Starter bundle architecture handoff

Status: design and source inspection only, 19 November 2026. No production implementation, deployment, device change, or paid activation is represented by this handoff.

## Repository fit

At `6b569ad4df1736cadeb9137124832895578cb3e6`, this repository is an artwork-backed static GitHub Pages interface. Its only current integration is browser clipboard generation. It has no Phone MCP client, Android dispatcher, relay, service, job persistence, authorization server, backend API, build manifest, or tests. The approved issue requires stopping code edits if the repository is a poor fit. Adding a new runner here would duplicate an unknown production stack and cannot repair the reported devices. No app files are modified by this handoff.

The current phone command implementation, exact installed Pi source and launcher, and ownership of the parallel-session transport must be recovered before the faults can be fixed. A direct Phone MCP catalog is not evidence of the Pi service source, registry or grant. The issue's historical positive and negative observations are not reproduced in this checkout.

## Reconciled source evidence

- [Issue 1 and its diagnostic comment](https://github.com/segunayoade/malkuth-control-hub/issues/1) describe 0.19.0 `start_app` argument errors, `session_create` dispatch failure, focus loss, and parallel transport disconnect despite general connected status. Codex Cloud task submission was not confirmed.
- [Spatial lab draft PR 9](https://github.com/segunayoade/ascension-spatial-lab-/pull/9) reports the original two MCP3 artifacts were subsequently recovered and hash-matched. Its [reconciliation record](https://github.com/segunayoade/ascension-spatial-lab-/blob/616880793a01502a154f5849e9c126985e69b211/docs/ascension/MCP3_CONTROL_RECONCILIATION_20261119.md) records offline inspection, five simulated channel tests, a physical Site v8 status-card check, and the need for a fresh installed-Pi source capture. These are reported evidence, not tests rerun here. The old rollout is not a candidate for the current full-control service and must not be executed.
- Site v8's correlated upstream response is not a Pi-to-phone receipt or a signed handset identity. Site `phone.read` and direct phone control are distinct grants. Preserve their scopes and all current functionality.

## Repair sequence in the owning source

1. Locate the maintained Android Phone MCP client/server, command dispatcher, relay and installed Pi source/launcher through an authorised read-only route. Record source provenance, catalog version, deployed hashes and owner; avoid collecting secrets. Preserve existing grants and sessions.
2. Compare advertised `start_app` and `session_create` schemas against the actual client serialization, relay envelope and server dispatch. Add integration tests for the exact observed requests and typed argument/unknown-command errors. Do not classify these failures as permission denials without evidence.
3. Require a parallel session's owned display, session ID, lease, package and window identity before launch or interaction; fail clearly when ownership or readiness changes. Do not depend on the primary display or infer transport readiness from general health.
4. On reconnect, re-establish transport, refresh catalog, session and lease state, invalidate stale requests, and require an explicit idempotent restart. Never silently replay an uncertain launch, text entry or submit. Record metadata-only diagnostics; do not include screen contents or prompt text.
5. For Codex Cloud, verify in order: isolated Chrome session and `https://chatgpt.com/codex/cloud`, observed editable field, approved draft, text readback, explicit separately authorised submission, and confirmed task ID/link. A page or draft is not a submitted task. The destination UI and acceptance must be re-observed because they can change.

## Starter bundle integration design

The machine-readable [capability manifest](starter-capabilities.json) is a planning inventory, not a live discovery result. Reuse the existing Bridge and Phone MCP; put orchestration in the actual service owner after its boundaries are established. Do not create another Cloudflare deployment stack or presume Termius SSH credentials.

The proposed runner contract has a durable job ID and idempotency key, explicit owner and bounded action/scope, expiring consent, a checkpoint and retry budget, and separately recorded attempt and evidence IDs. A job moves through proposed, awaiting approval, queued, running, paused, succeeded, failed or cancelled. A restart reconciles persisted checkpoints and adapter state before retry; uncertain side effects require explicit review. Cancellation and revocation fence future actions. A missing optional adapter is unavailable, never silently successful. Receipts identify the observer, time, operation, scope, outcome and evidence provenance without secrets or private screen content.

Adapter boundary: B01 reads authorised Pi operational data; B02 prepares an existing Cloudflare deployment for separate approval; B03 provides an optional notification interface; B05 owns bounded durable scheduling; B06 exposes the authenticated, scoped hub interface; B07 remains a human-operated Termius fallback; B08 records service-health and evidence provenance. None is implemented or connected by this handoff. Mutations, deployment and account changes require their own explicit approvals.

## Skills and acceptance gates

Author C01 capability inventory (inspect and label evidence), C02 Pi incident response (read-only triage and preserve service), C03 phone navigation (window ownership and consent), C04 Quest regression (checklist only), C05 release provenance and rollback, C06 nightly queue supervision (bounded and approved operations), and C07 permission and approval ledger in the repository that owns their execution. Each must name its inputs, prohibited actions, evidence and escalation; a document alone grants no powers.

Before a draft implementation can be accepted, demonstrate schema/dispatcher regression, same- and independent-session behavior, stale transport refusal and recovery, consent denial, idempotency, replay fencing, retries, cancellation, interrupted-job recovery, independent evidence, redaction, and a mock end-to-end task. Preserve existing app and Pi tests. A physical phone journey, authenticated deployment, new OAuth consent, paid service, or Pi modification remains a separate approval and verification step.

## Recovery

The branch containing this handoff is documentation-only. Revert these documentation files to roll it back; do not touch production systems. Next obtain the owning source locations and a current, authorised, secret-free read-only Pi source capture, then implement and test at those boundaries before proposing deployment. Keep PR 9 unmerged and avoid replacing its work.
