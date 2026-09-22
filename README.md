# Tim Okito

I test whether AI safety and observability tools actually do what their
documentation claims, and I publish the results either way.

The pattern that started this: standard monitoring reliably reports
healthy systems while AI applications fail underneath it. Agents break
and emit green spans. Retrieval collapses and dashboards stay clean.
Guardrails block the wrong things and every trace reads as a successful
policy match. Finding these failures requires building evaluation layers
that know what the answer should have been, so that is what these labs
build, with the Terraform, test harnesses, and raw results included so
anyone can rerun or challenge the findings.

## The labs

| Lab | Question | What I found |
|---|---|---|
| [Bedrock Guardrails efficacy](https://github.com/ptokito/bedrock-guardrails-lab) | Does a guardrail block what its configuration says, and only that? | Four of five benign educational questions incorrectly blocked while all seventeen adversarial prompts were caught. Rewriting the topic definition changed nothing, pointing to configured examples as the classification driver. |
| [Kubernetes security observability](https://github.com/ptokito/k8s-security-observability-lab) | Can a hardened cluster be built and verified with least privilege end to end? | Terraform-provisioned k3s with Pod Security Admission, least-privilege RBAC, default-deny NetworkPolicy, and a CI/CD pipeline gated on Trivy vulnerability scanning. |
| [RAG observability](https://github.com/ptokito/rag-observability-lab) | Does standard tracing catch a retrieval-quality failure? | No. Low-relevance retrieval produced confidently wrong answers while every span stayed healthy. A custom evaluation layer surfacing retrieval confidence caught what the tracing missed. |
| Agent tool-call reliability | Do agent failures show up in telemetry? | Five of six injected failure modes produced healthy spans. Redesigning tool interfaces and error semantics moved task success from one in three runs to three in three. |
| CloudWatch investigation agent | Can an agent reliably investigate real logs? | Tool design, not model capability, was the constraint. Fixing tool contracts took success from intermittent to consistent. |

**Next:** instrumenting a Bedrock RAG application against the
OpenTelemetry GenAI semantic conventions to test whether spec-conformant
spans can diagnose a deliberately induced retrieval failure.

## Writing

Long-form write-ups are on [Dev.to](https://dev.to/ptokito), including
[the guardrails study](https://dev.to/ptokito/i-tested-whether-a-bedrock-guardrail-blocks-the-right-things-it-blocked-a-math-question-54hn).
Shorter posts on [LinkedIn](https://linkedin.com/in/timokito).

## Background

Ten-plus years in enterprise customer-facing technical roles at
Dynatrace, GitLab, and New Relic. PMP. AWS Certified AI Practitioner.
AWS Solutions Architect Associate. HashiCorp Terraform Associate. KCSA.
Currently pursuing the AIGP (AI Governance Professional).
