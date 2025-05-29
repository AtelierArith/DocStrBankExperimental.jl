```
list_problems(repository, domain)
list_problems(repository, collection, domain)
```

計画 `repository` から特定の `domain` の問題をリストします。一部のリポジトリでは、ドメインも `collection` に整理されています。

現在サポートされているリポジトリは次のとおりです：

  * [`JuliaPlannersRepo`](@ref): JuliaPlanners 組織によって維持されているリポジトリ
  * [`IPCInstancesRepo`](@ref): 国際計画コンペティションのドメインと問題
  * [`PlanningDomainsRepo`](@ref): http://planning.domains/ によって提供されるリポジトリ

各リポジトリのドキュメントを参照して、詳細情報を確認してください。
