<p align="center">
  <a href="https://syferit.soltrixstudios.com">
    <img src="assets/icon.png" alt="Syferit Logo" width="80" height="80" />
  </a>
</p>

<h1 align="center">Syferit Code Defense GitHub Action 🛡️</h1>

<p align="center">
  <strong>Universal Adversarial CI/CD Code Defense Action</strong><br>
  <em>&ldquo;Don&apos;t Just Ship it. Syferit.&rdquo;</em>
</p>

<p align="center">
  <a href="https://github.com/marketplace/actions/syferit-code-defense"><img src="https://img.shields.io/badge/Marketplace-Syferit%20Code%20Defense-blue?logo=github" alt="GitHub Marketplace" /></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/License-Apache%202.0-green.svg" alt="License" /></a>
  <a href="https://syferit.soltrixstudios.com"><img src="https://img.shields.io/badge/Ecosystem-Syferit-blue" alt="Syferit" /></a>
</p>

> Universal Adversarial Code Defense Action against Autonomous AI Reverse-Engineering Agents, MCP Decompiler Bridges, and Automated Clone Farms by **[Soltrix Studios](https://soltrixstudios.com)**.

---

## ⚡ What is this Action?

The official GitHub Action from **Soltrix Studios** that protects your software against unauthorized scraping, automated copying, and competitor cloning directly inside your CI/CD pipeline.

Run it on your production build artifacts (`./dist`, `./build`, or custom output folders) right before deployment. Your software continues to run fast, intact, and reliable while remaining completely unreadable and unreplicable to external tools or competitors.

### Why Developers Use Syferit

* **Zero Configuration Required:** Automatically protects JavaScript, TypeScript, WebAssembly, Python, and native builds out of the box.
* **Preserves Full Performance:** Zero noticeable runtime overhead. Your app executes exactly as fast as before.
* **Prevents Automated Cloning:** Competitors and automated tools cannot understand or reconstruct your proprietary application logic.
* **Drop-in CI/CD Step:** Adds in seconds to your existing GitHub Actions workflow.

---

## 🚀 Quickstart

Add this step to your GitHub Actions workflow after your build step:

```yaml
name: Production Release

on:
  push:
    tags:
      - 'v*.*.*'

jobs:
  build-and-protect:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Build Application
        run: |
          npm ci
          npm run build

      # 🛡️ Syferit Protection Pass
      - name: 🛡️ Protect Release with Syferit
        uses: soltrix-studios/syferit-action@v1
        with:
          target: './dist'
          preset: 'hardened'
          domain: 'saas'

      - name: Deploy Protected Artifacts
        run: ./scripts/deploy.sh ./dist
```

---

## 🛠️ Action Inputs

| Input | Description | Required | Default |
| :--- | :--- | :---: | :--- |
| `target` | Path to the directory or file to protect (e.g. `./dist`, `./build`, `./app.py`). | **Yes** | `./dist` |
| `output` | Destination output directory or file. If omitted, target is protected in-place. | No | `""` (In-place) |
| `preset` | Protection level: `standard`, `hardened`, or `maximum`. | No | `'hardened'` |
| `domain` | Industry vocabulary matching: `saas`, `fintech`, `security`, `gaming`. | No | `'saas'` |
| `seed` | Optional seed value for reproducible builds across releases. | No | `""` (Auto-generated) |
| `node-version` | Node.js version used to execute the Syferit engine. | No | `'22'` |

---

## 📊 Action Outputs

| Output | Description |
| :--- | :--- |
| `protected-count` | Total number of files successfully hardened by Syferit. |
| `status` | Execution status (`success` or `failure`). |

---

## 🌟 Framework Examples

### Vite / React / Vue / Svelte
```yaml
- name: Protect Vite Output
  uses: soltrix-studios/syferit-action@v1
  with:
    target: './dist'
    preset: 'hardened'
```

### Next.js Production Build
```yaml
- name: Protect Next.js Bundles
  uses: soltrix-studios/syferit-action@v1
  with:
    target: './.next'
    preset: 'hardened'
```

### Electron Desktop Release
```yaml
- name: Protect Electron Bundles
  uses: soltrix-studios/syferit-action@v1
  with:
    target: './dist/mac'
    preset: 'maximum'
```

### Python Backend / AI Model Pipeline
```yaml
- name: Protect Python Modules
  uses: soltrix-studios/syferit-action@v1
  with:
    target: './src'
    output: './dist-protected'
    preset: 'maximum'
    domain: 'security'
```

---

## 📋 Job Summaries

Every run automatically generates a clean status summary in your GitHub Actions console, confirming the target files, protection status, and run details.

---

## 📄 License & Support

- **License:** [Apache-2.0](https://github.com/soltrix-studios/syferit-action/blob/main/LICENSE) © Soltrix Studios
- **Official Website:** [https://syferit.soltrixstudios.com](https://syferit.soltrixstudios.com)
- **Framework Core:** [https://github.com/soltrix-studios/syferit](https://github.com/soltrix-studios/syferit)
- **Support & Issues:** [https://github.com/soltrix-studios/syferit-action/issues](https://github.com/soltrix-studios/syferit-action/issues)
