```
load_problem(repository, domain, problem)
load_problem(repository, collection, domain, problem)
```

計画 `repository` から指定された名前またはインデックスの問題を特定の `domain` に対してロードします。一部のリポジトリでは、ドメインも `collection` に整理されています。

現在サポートされているリポジトリは次のとおりです：

  * [`JuliaPlannersRepo`](@ref): JuliaPlanners組織によって維持されているリポジトリ
  * [`IPCInstancesRepo`](@ref): 国際計画コンペティションのドメインと問題
  * [`PlanningDomainsRepo`](@ref): http://planning.domains/ によって提供されるリポジトリ

各リポジトリのドキュメントを参照して、詳細情報を確認してください。
