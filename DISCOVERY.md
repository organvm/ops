# Discovery: organvm/ops

**organvm/ops is the always-on operations backbone of the a-organvm estate — and it is already working.**

This repo is plane (i) of a deliberate three-plane scheduling model: GitHub Actions cron workflows that run 24/7 regardless of whether any local machine is awake. It ships two durable capabilities today: a daily org-wide GitHub hygiene report (open PRs, staleness, open issues across all repos, committed to `reports/`) and a weekly keepalive that prevents GitHub's 60-day auto-disable from silencing the cron layer and self-heals any workflow GitHub already disabled for inactivity. Every workflow bookends each run with machine-readable `start`/`end` TSV lines in `bookends/`, which feed the sibling `ops-witness` cross-plane audit surface. The bookend contract, stagger rules, and keepalive/re-enable pattern are all reusable primitives the rest of the estate can adopt directly. The highest-value first task is **wiring the hygiene report into ops-witness** so stale repos surface as actionable signals rather than just committed markdown — closing the loop between observation (plane i) and judgment (plane iii).

_Discovered 2026-06-22. Not archival — active operational infrastructure._
