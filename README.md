# AntiShiJianKey
在github workflow视奸别人的令牌太坏了，我要反对这一点！

在公共仓库中。绝对不能将 API 密钥或其他敏感凭证直接写入你的代码或配置文件（如 update-readme.yml），因为它们会暴露在你的公共仓库历史记录中。

GitHub 提供了一个安全的方式来处理这个问题，叫做 GitHub Secrets。

什么是 GitHub Secrets？

GitHub Secrets 是一种让你存储敏感信息（如 API 密钥、密码、访问令牌）的方式，这些信息可以被你的 GitHub Actions 工作流安全地使用，而不会暴露在你的代码库中。

它们在存储时是加密的。

它们只在工作流运行时暴露给选定的 Actions 或作为环境变量注入到运行器（Runner）中。

它们的值不会显示在工作流的日志中（GitHub 会尝试自动屏蔽它们，但你仍应避免在脚本中明确打印它们）。

如何在公共仓库中安全地使用 API Key：

获取你的 API Key：首先，你需要从你选择的 LLM 服务提供商那里获取 API Key。

在 GitHub 仓库中创建 Secret：

进入你的 GitHub 仓库页面。

点击顶部的 "Settings" 标签页。

在左侧边栏，找到 "Security" 部分，点击 "Secrets and variables" 下的 "Actions"。

点击右上角的 "New repository secret" 按钮。

Name：给你的 Secret 起一个名字。这个名字将在你的工作流文件中引用。按照惯例，通常使用大写字母和下划线，例如 LLM_API_KEY 或 OPENAI_API_KEY。

Secret / Value：将你从服务提供商那里获得的实际 API Key 粘贴到这里。确保没有多余的空格或字符。

点击 "Add secret"。

在你的 GitHub Workflow 中使用 Secret：

打开你的工作流文件（例如 .github/workflows/update-readme.yml）。

你可以通过 ${{ secrets.YOUR_SECRET_NAME }} 语法来访问你创建的 Secret。

通常，你会将 Secret 的值赋给一个环境变量，或者直接作为参数传递给某个 Action 或脚本。
