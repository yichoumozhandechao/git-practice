"# Git ʵ��" 
# Git 学习与实践

## 学习资料来源
- 官方文档：https://git-scm.com/doc
- 廖雪峰 Git 教程：https://www.liaoxuefeng.com/wiki/896043488029600
- GitHub 入门：https://docs.github.com/zh/get-started
- Pro Git 中文版：https://git-scm.com/book/zh/v2

## 实践流程

### 1. 安装与配置 Git
- 从官网下载 Git 并安装，使用 `git --version` 验证。
- 通过 `git config` 设置全局用户名和邮箱，配置默认分支名 `main`。
- 解决 Windows 换行符问题：`git config --global core.autocrlf true`。

### 2. 创建本地仓库
- 建立项目目录 `my-git-practice`，使用 `git init` 初始化。
- 创建 `README.md`、`src/main.py` 等初始文件。

### 3. 进行 3 次有效提交
- **第 1 次提交**：初始化项目结构，添加 README 和主程序入口。
- **第 2 次提交**：实现 `greet` 函数，增强程序功能。
- **第 3 次提交**：添加 `.gitignore` 文件，用于忽略缓存和日志。

### 4. 远程仓库操作
- 在 GitHub 上注册账号并创建公开仓库 `git-practice`。
- 使用 `git remote add origin` 关联远程仓库。
- 通过 `git push -u origin main` 将全部提交推送到远程。

## 每次提交的主要内容说明
| 提交次序 | 提交信息 | 修改内容 |
| 第一次 | 初始化项目：添加 README 和主程序入口 | 新建 README.md、src/main.py |
| 第二次 | 新增 greet 函数并修改主程序输出 | 在 main.py 中添加函数并调整调用 |
| 第三次 | 添加 .gitignore 忽略缓存和日志文件 | 新建 .gitignore，忽略 __pycache__ 和 *.log |

## 遇到的问题及解决方法

### 问题 1：`git push` 时提示权限被拒绝
- **现象**：`Permission denied (publickey)` 或 `remote: Invalid username or password.`
- **原因**：使用 SSH 地址推送，但本地未配置 SSH Key；或使用 HTTPS 地址但密码失效。
- **解决**：切换为 HTTPS 地址并配置个人访问令牌（Token）。在 GitHub 设置里生成 Personal Access Token，推送时用户名填 GitHub 用户名，密码填 token。或者改用 HTTPS + 凭据管理器存储。

### 问题 2：本地默认分支名为 `master`，而远程默认使用 `main`
- **现象**：推送时提示 `error: src refspec master does not match any`，或者推送后远程有两个分支。
- **原因**：`git init` 未配置 `init.defaultBranch`，本地分支仍为 `master`。
- **解决**：重命名本地分支为 `main`：`git branch -M main`，再执行 `git push -u origin main`。若失败，先 `git remote -v` 检查远程地址，再重试。

### （补充问题）问题 3：commit 后忘记添加文件，想修改提交信息
- **现象**：提交后才发现漏了文件或提交说明错误。
- **解决**：使用 `git commit --amend` 可以修改最近一次提交的内容和信息，修改后需要 `git push --force-with-lease` 谨慎推送（仅在个人分支上操作）。

## Git 学习心得
通过本次实践，我掌握了 Git 的基本工作流：**工作区 → 暂存区 → 本地仓库 → 远程仓库**。理解了 `add`、`commit`、`push` 等核心命令的意义，体会到版本控制对代码管理的巨大价值。它能清晰地记录每一次修改，方便回溯和协作。在配置和推送过程中遇到的错误也让我学会了查阅文档和常见解决方案，对远程仓库的身份验证机制有了初步认识。今后我会在更多项目中坚持使用 Git，养成细粒度、有意义的提交习惯，并进一步学习分支管理和协作工作流。
