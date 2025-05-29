```
load_domain(repository, domain)
load_domain(repository, collection, domain)
```

プランニング `repository` からドメインをロードします。一部のリポジトリでは、ドメインは `collection` にも整理されています。

現在サポートされているリポジトリは次のとおりです：

  * [`JuliaPlannersRepo`](@ref): JuliaPlanners組織によって維持されているリポジトリ
  * [`IPCInstancesRepo`](@ref): 国際プランニングコンペティションのドメインと問題
  * [`PlanningDomainsRepo`](@ref): http://planning.domains/ によって提供されるリポジトリ

各リポジトリのドキュメントを参照して、詳細情報を確認してください。
