# mlops-templates (fork)

Fork of [`Azure/mlops-templates`](https://github.com/Azure/mlops-templates), maintained as the shared pipeline library for a small MLOps v2 factory — see [`rubyrayjuntos/azure-mlops`](https://github.com/rubyrayjuntos/azure-mlops) for the full architecture writeup and the first project generated from this factory.

## What's different from upstream

- Marketplace actions (`azure/login`, `actions/checkout`) pinned to commit SHAs across all workflow files that use them — upstream floats on major-version tags.
- `read_yaml_action/index.js`: fixed a boolean-parsing bug where `Boolean(anyNonEmptyString)` always evaluated `true`, silently forcing `enable_monitoring`/`enable_aml_computecluster` regardless of config.
- `tf-gha-install-terraform.yml` and `read-yaml.yml` already carry these fixes and are referenced by consuming projects via `@main` (not a pinned SHA — see the architecture doc linked above for why that's deliberate for this fork specifically, vs. the marketplace-action pins above).

## Usage

Reference workflows here as `uses: rubyrayjuntos/mlops-templates/.github/workflows/<name>.yml@main` from a project's own pipeline files. Requires the project's repo to have `AZURE_CLIENT_ID` / `AZURE_TENANT_ID` / `AZURE_SUBSCRIPTION_ID` secrets and an OIDC federated credential set up for the calling app registration.

---

[Upstream accelerator README](https://github.com/Azure/mlops-v2/blob/main/README.md)
