# Repository Guidelines

## Project Structure & Module Organization
- This repo stores packaged Helm charts only (no chart source).
- Put `.tgz` files under `packages/`. GitHub Pages serves content from the `gh-pages` branch.
- CI publishes `packages/*.tgz` and generates `index.yaml` into `gh-pages`.

## Publish & Maintenance
- Add or update a package by committing a new `.tgz` to `packages/` on `main/master`.
- The workflow `.github/workflows/release.yml` syncs files to `gh-pages` and rebuilds the index with the correct `--url`.
- Keep all historical versions. Do not overwrite existing `.tgz` files; bump chart versions instead.

## Client Usage
- Add repo: `helm repo add myrepo https://<owner>.github.io/<repo>`
- Install chart: `helm install demo myrepo/<chart> --version <x.y.z>`

## Commit & Pull Request Guidelines
- Use concise messages describing the package change (e.g., `release(example): 0.2.0`).
- PRs should list added/removed `.tgz` and intended public URL.
- Ensure filenames follow `<name>-<version>.tgz` and version is semver.

## Security & Operations
- This repo is public content hosting; do not store secrets.
- If deprecating a chart, keep the old packages but update your external docs to reflect status.

## Agent-Specific Instructions
- Do not add chart source or templating logic here.
- Changes should be limited to `packages/`, workflow, and docs required for hosting.
