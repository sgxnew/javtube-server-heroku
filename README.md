# JavTube Server Heroku

## ‼️置顶
> **Heroku Update**
>
>Starting November 28th, 2022, free Heroku Dynos, free Heroku Postgres, and free Heroku Data for Redis® will no longer be available.
If you have apps using any of these resources, you must upgrade to paid plans by this date to ensure your apps continue to run and to retain your data. For students, we will announce a new program by the end of September.

Heroku不再免费，请使用Docker部署后端，或使用[Koyeb快速部署](https://github.com/javtube/javtube-server-koyeb)。

## 项目介绍

<!-- [![Heroku](https://img.shields.io/badge/heroku-%23430098.svg?style=flat-square&logo=heroku&logoColor=white)](https://heroku.com)
[![License](https://img.shields.io/github/license/javtube/javtube-server-heroku?style=flat-square&logo=github&color=blue)](https://github.com/javtube/javtube-server-heroku/blob/main/LICENSE) -->

> - 部分新建的应用有可能需要科学访问，如果需要可以套一层Cloudflare CDN或Workers。
> - Heroku对免费账号存在如内存、冷启动等限制，但是对于个人部署使用JavTube后端项目理论上是足够的，具体可以参考[Pricing](https://www.heroku.com/pricing)。

使用本仓库可以快速将`JavTube`后端~~免费~~部署至[`Heroku`](https://heroku.com)云平台。

## 一键部署

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)
[![Deploy](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA5MCA5MCI+PGRlZnM+PHN0eWxlPi5hLC5ie2ZpbGw6I2ZmZjt9LmIsLmN7b3BhY2l0eTowLjU7fTwvc3R5bGU+PC9kZWZzPjx0aXRsZT5pY29uLWRvY2tlci1maWxsPC90aXRsZT48cGF0aCBjbGFzcz0iYSIgZD0iTTc4LjcxLDQ5LjM5SDc2LjQ5bDAtMi4zQTcuMTgsNy4xOCwwLDAsMCw2OS4zMiw0MGgtLjI0VjQ4LjVhMy43NiwzLjc2LDAsMCwxLTMuNzUsMy43NUg0LjgxdjYuNjdBMjUuNzcsMjUuNzcsMCwwLDAsMzAuNTUsODQuNjZoOS4zMmEyNy4xNiwyNy4xNiwwLDAsMCwyNC41Ny0xNWMuNjEtMS4yLDEuNzUtMy40MywyLjI3LTQuNjgsMy4yOC04LDQuNTQtOC41NCwxMC04LjU4bDguNDQsMHYtLjI0Qzg1LjE5LDUyLjExLDgyLjU5LDQ5LjM5LDc4LjcxLDQ5LjM5Wk0yNi45Miw2Ny43MmEyLjQ2LDIuNDYsMCwwLDEsNC45MiwwLDIuNDYsMi40NiwwLDAsMS00LjkyLDBaIi8+PHJlY3QgY2xhc3M9ImEiIHg9IjIyLjAyIiB5PSIzNyIgd2lkdGg9IjExLjg3IiBoZWlnaHQ9IjExLjg3IiByeD0iMS4yOCIvPjxyZWN0IGNsYXNzPSJhIiB4PSI2LjMxIiB5PSIzNyIgd2lkdGg9IjExLjg3IiBoZWlnaHQ9IjExLjg3IiByeD0iMS4yOCIvPjxyZWN0IGNsYXNzPSJhIiB4PSI1My40NCIgeT0iMzciIHdpZHRoPSIxMS44NyIgaGVpZ2h0PSIxMS44NyIgcng9IjEuMjgiLz48cmVjdCBjbGFzcz0iYSIgeD0iMzcuNzMiIHk9IjIxLjI5IiB3aWR0aD0iMTEuODciIGhlaWdodD0iMTEuODciIHJ4PSIxLjI4Ii8+PHBhdGggY2xhc3M9ImIiIGQ9Ik03OC43MSw0OS4zOUg3Ni40OWwwLTIuM0E3LjE4LDcuMTgsMCwwLDAsNjkuMzIsNDBoLS4yNFY0OC41YTMuNzYsMy43NiwwLDAsMS0zLjc1LDMuNzVINC44MXY2LjY3QTI1Ljc3LDI1Ljc3LDAsMCwwLDMwLjU1LDg0LjY2aDkuMzJhMjcuMTYsMjcuMTYsMCwwLDAsMjQuNTctMTVjLjYxLTEuMiwxLjc1LTMuNDMsMi4yNy00LjY4LDMuMjgtOCw0LjU0LTguNTQsMTAtOC41OGw4LjQ0LDB2LS4yNEM4NS4xOSw1Mi4xMSw4Mi41OSw0OS4zOSw3OC43MSw0OS4zOVpNMjYuOTIsNjcuNzJhMi40NiwyLjQ2LDAsMCwxLDQuOTIsMCwyLjQ2LDIuNDYsMCwwLDEtNC45MiwwWiIvPjxyZWN0IGNsYXNzPSJhIiB4PSIyMi4wMiIgeT0iMzciIHdpZHRoPSIxMS44NyIgaGVpZ2h0PSIxMS44NyIgcng9IjEuMjgiLz48cmVjdCBjbGFzcz0iYSIgeD0iNi4zMSIgeT0iMzciIHdpZHRoPSIxMS44NyIgaGVpZ2h0PSIxMS44NyIgcng9IjEuMjgiLz48cmVjdCBjbGFzcz0iYSIgeD0iNTMuNDQiIHk9IjM3IiB3aWR0aD0iMTEuODciIGhlaWdodD0iMTEuODciIHJ4PSIxLjI4Ii8+PHJlY3QgY2xhc3M9ImEiIHg9IjM3LjczIiB5PSIyMS4yOSIgd2lkdGg9IjExLjg3IiBoZWlnaHQ9IjExLjg3IiByeD0iMS4yOCIvPjxnIGNsYXNzPSJjIj48cmVjdCBjbGFzcz0iYSIgeD0iMzcuNDkiIHk9IjM2Ljc2IiB3aWR0aD0iMTIuMzUiIGhlaWdodD0iMTIuMzUiIHJ4PSIxLjUyIi8+PC9nPjxnIGNsYXNzPSJjIj48cmVjdCBjbGFzcz0iYSIgeD0iMjEuNzgiIHk9IjIxLjA1IiB3aWR0aD0iMTIuMzUiIGhlaWdodD0iMTIuMzUiIHJ4PSIxLjUyIi8+PC9nPjxnIGNsYXNzPSJjIj48cmVjdCBjbGFzcz0iYSIgeD0iMzcuNDkiIHk9IjUuMzQiIHdpZHRoPSIxMi4zNSIgaGVpZ2h0PSIxMi4zNSIgcng9IjEuNTIiLz48L2c+PC9zdmc+)](https://render.com/deploy)

## 具体说明

> 以下步骤需要登录Heroku账号，没有账号的可以先进行[注册](https://signup.heroku.com/)。

- [部署应用](#部署应用)
- [更新应用](#更新应用)
- [删除应用](#删除应用)

### 部署应用

- 点击本页面中的[一键部署](#一键部署)按钮创建app。

![deploy](images/deploy.png)

- 在`App name`中输入自定义的应用名。
- **建议**将地区选择为`United States`。
- 在`Config Vars`中输入新的`TOKEN`并**复制**。
- 点击`Deploy app`完成部署。

![create](images/create.png)

- 右键**复制**View中的`JavTube Server URL`链接地址。

![view](images/view.png)

- 可以点击View，出现类似如下的页面即为部署成功。

![page](images/page.png)

- 在JavTube插件中分别粘贴进之前复制的`JavTube Server URL`与`TOKEN`以完成插件配置。

![plugin](images/plugin.png)

### 更新应用

> 本节仅当有更新需求时参考。

- 点击本仓库右上方的`Fork`按钮。

![fork](images/fork.png)

- 点击`Create fork`。

![create-fork](images/create-fork.png)

- 如果**之前已经Fork过**本仓库，则选择`Fetch upstream -> Fetch and merge`，**否则跳过此步骤**。

> 建议每次在更新后端之前，都尝试`Fetch and merge`以与源仓库保持同步。

![fetch-merge](images/fetch-merge.png)

- 然后进入[Heroku Dashboard](https://dashboard.heroku.com/apps)，选择之前部署的应用。

![dashboard](images/dashboard.png)

- 在Dashboard中，选择`Deploy`。

![overview-deploy](images/overview-deploy.png)

- 在`Deploy`中，选择`GitHub`并点击`Connect to GitHub`。

![deploy-github](images/deploy-github.png)

- 在弹出的页面中，点击`Authorize Heroku`。

![auth-heroku](images/auth-heroku.png)

- 按如下步骤连接之前Fork的仓库。

![connect-repo](images/connect-repo.png)

- 点击`Deploy Branch`，即可完成更新。

> 后续更新后端也只需要点击`Deploy Branch`即可。

![deploy-branch](images/deploy-branch.png)

- 如下图所示，即表示已完成更新。

![deployed](images/deployed.png)

> PS：当然也可以直接通过**删除**并**重新创建**应用来进行更新，但是注意`app name`和`token`需要和之前保持一致。

### 删除应用

> ⚠本节会删除之前部署的应用导致后续刮削请求失败。除非有明确需求（例如重新部署应用），否则请略过。

- 进入[Heroku Dashboard](https://dashboard.heroku.com/apps)，点击需要删除的应用。

![dashboard](images/dashboard.png)

- 点击设置`Settings`。

![overview-settings](images/overview-settings.png)

- 拉到设置最底部，点击`Delete app`。

![settings](images/settings.png)

- 按提示，重新输入一遍应用名以删除应用。

![delete](images/delete.png)
