```
persistent_homology(lc::LefschetzComplex, filtration::Vector{Int})
```

Lefschetz複体のフィルトレーションに対する持続ホモロジーを完成させます。このフィルトレーションは、Lefschetz複体の境界行列に関連する体上で定義されています。

関数は次の2つの値を返します。

  * `phsingles::Vector{Vector{Int}}`
  * `phpairs::Vector{Vector{Tuple{Int,Int}}}`

これは、フィルトレーション値によって与えられた順序が許容されることを前提としています。すなわち、置換された境界行列は厳密に上三角です。この関数は、`phsingles`に無限長持続区間の開始フィルトレーション値を返し、`phpairs`に有限長持続区間の出生および死亡フィルトレーション値を返します。
