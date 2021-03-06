## <a name="pull-request-processing"></a>拉取请求处理

之前的部分介绍了提交建议更改的过程，提交时所用的方式是将建议更改绑定在已添加到目标存储库拉取请求队列的新拉取请求 (PR) 中。 拉取请求通过请求将工作分支的更改拉取和合并到其他分支，从而实现 GitHub 的协作模型。 大多数情况下，其他分支就是主存储库中的默认/主分支。

### <a name="validation"></a>验证

拉取请求在可以合并到其目标分支前，可能需要通过一个或多个 PR 验证过程。 验证过程因建议更改的范围和目标存储库的规则而异。 拉取请求提交后，可能会遇到以下一种或多种情况：

- **可合并性**：首先进行基准 GitHub 可合并性测试，验证分支中的建议更改是否与目标分支冲突。 如果拉取请求指示未通过该测试，则必须协调导致合并冲突的内容，然后才能继续进行处理。
- **CLA**：如果将内容提交到公共存储库并且你不是 Microsoft 员工，根据建议更改的规模，你可能需要在首次向该存储库提交拉取请求时完成简短的贡献许可协议 (CLA)。 完成 CLA 步骤后，才会处理拉取请求。
- **标记**：标签会自动应用于拉取请求，用于指示拉取请求在通过验证工作流程时的状态。 例如，新的拉取请求可能会自动接收“不合并”标签，指示该拉取请求尚未完成验证、审阅和注销步骤。
- **验证和生成**：自动检查将验证更改是否通过验证测试。 验证测试可能生成警告或错误，你需要对拉取请求中的一个或多个文件进行更改，然后才能将其合并。 验证测试结果将以备注的形式添加到拉取请求中供你审阅，可通过电子邮件发送给你。
- **过渡**：受更改影响的文章页面会自动部署到过渡环境，供验证和生成成功后进行审阅。 PR 备注中包含预览 URL。
- **自动合并**：拉取请求在通过验证测试并满足某些条件后可能会进行自动合并。 在这种情况下，不需要执行其他操作。

### <a name="review-and-sign-off"></a>审阅和注销

所有 PR 处理完成后，应审阅结果（PR 备注、预览 URL 等），在签核合并前决定是否需要对其文件进行其他更改。 PR 审阅者审阅拉取请求后，如果存在明显的问题需在合并前解决，审阅者还可通过备注提供反馈。

[!INCLUDE[contribute-how-to-pull-requests-apex-automation.md](contribute-how-to-pull-requests-apex-automation.md)]

拉取请求没有问题并签核后，更改将合并回父分支并关闭拉取请求。

### <a name="publishing"></a>发布

请记住，拉取请求必须由 PR 审阅者进行合并，然后更改才能包括在下个计划发布运行中。 拉取请求通常按提交顺序审阅/合并。 如果拉取请求需针对特定发布运行进行合并，你需要提前与 PR 审阅者合作，确保在发布前进行合并。

供稿内容在得到批准并进行合并后，Docs.Microsoft.Com 发布过程会选取这些内容。 发布时间可能不同，具体取决于管理内容被提交到的存储库的团队。 以下路径下发布的文章通常部署时间约为太平洋时间星期一到星期五上午 10:30 和下午 3:30：

- https://docs.microsoft.com/azure/
- https://docs.microsoft.com/aspnet/
- https://docs.microsoft.com/dotnet/
- https://docs.microsoft.com/enterprise-mobility-security

文章发布后出现在网上最多耗时 45 分钟。 文章发布后，可在相应 URL 处验证更改：`https://docs.microsoft.com/<path-to-your-article-without-the-md-extension>`。
