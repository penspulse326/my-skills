---
name: nodejs-setup
description: Node.js 環境建置與專案初始化
---

## 環境建置與專案初始化
前端或後端專案，只要使用 Node.js 作為執行環境，就評估是否需要進行以下相關設定

💡 **初始化前置作業**：
- **.gitignore**：建立標準 Git 忽略清單。
- **Node 版本鎖定**：配置 `.nvmrc` 並在 `package.json` 中宣告 `engines`（如使用 pnpm 則忽略此步驟）
- **編輯器配置 💡**：建立 `.vscode/settings.json` 與 `extensions.json` 實現「存檔即自動修復與格式化」

## 品質管理套件

安裝以下套件：

- **Prettier**：根據專案類型，選擇適合的 Prettier 規範，並建立 `.prettierignore` 💡
- **ESLint**：根據專案類型，選擇適合的 ESLint 規範（必裝 Perfectionist），**並搭配 `eslint-config-prettier` 避免規則衝突 💡**
- **Commitlint**：使用通用的 Commit Message 規範
- **Husky**：安裝 Husky 並啟用 pre-commit 與 commit-msg hooks，確保每次提交前都會執行 Lint 與測試，並檢查 Commit Message 是否符合規範

## Git Hooks

commit 時應執行：
- lint-staged，確保提交的程式碼符合 ESLint/Prettier/Stylelint 規範 💡（僅針對暫存檔案，提升速度）

push 時應執行：
- test，確保提交的程式碼通過測試（如果有安裝測試框架）
- build，確保提交的程式碼能夠成功編譯

## Optional

### TypeScript

- 如專案使用 TypeScript，則需設定別名解析，以 `@` 作為 src 目錄的別名，並確保可以正常使用該別名進行撰寫與編譯

### 前端

- 如專案未使用 Tailwind CSS，則需安裝 Stylelint，確保 CSS/SCSS/LESS 等樣式檔案符合規範
- 如專案使用 Tailwind CSS，則
  - 在 ESLint 中安裝 Tailwind CSS 相關的規則，為 className 規則保護
  - 在 Prettier 中安裝 Tailwind CSS 相關的規則，確保 className 排序