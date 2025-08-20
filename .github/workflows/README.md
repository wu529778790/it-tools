# GitHub Pages 部署说明

本项目已配置 GitHub Actions 自动部署到 GitHub Pages。

## 配置步骤

### 1. 启用 GitHub Pages

1. 前往你的仓库设置 (Settings)
2. 在左侧菜单中找到 "Pages"
3. 在 "Source" 部分选择 "GitHub Actions"

### 2. 设置环境变量（如果需要）

如果你的仓库名称不是 `username.github.io` 格式，你可能需要设置 `BASE_URL` 环境变量：

1. 前往仓库设置 (Settings)
2. 在左侧菜单中找到 "Environments"
3. 点击 "New environment" 创建名为 `github-pages` 的环境
4. 在环境变量中添加：
   - Name: `BASE_URL`
   - Value: `/repository-name/` (替换为你的仓库名称)

### 3. 工作流程说明

当你推送代码到 `main` 分支时，GitHub Actions 会：

1. 安装项目依赖 (使用 pnpm)
2. 构建项目 (`pnpm run build`)
3. 部署到 GitHub Pages

### 4. 查看部署状态

- 前往仓库的 "Actions" 标签页查看构建状态
- 前往仓库设置中的 "Pages" 查看部署的 URL

## 故障排除

如果部署失败，请检查：

1. 确保 `main` 分支存在
2. 确保 `pnpm-lock.yaml` 文件存在且有效
3. 确保构建命令 `pnpm run build` 能成功运行
4. 确保 `dist` 目录被正确生成

## 自定义配置

如需修改构建配置，可以编辑 `.github/workflows/deploy.yml` 文件。

如需修改项目的基础路径，可以在仓库设置中添加 `BASE_URL` 环境变量。
