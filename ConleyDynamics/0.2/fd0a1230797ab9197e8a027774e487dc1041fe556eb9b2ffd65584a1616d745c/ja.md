```
persistent_homology(lc::LefschetzComplex, filtration::Vector{Int})
```

Lefschetz複体のフィルトレーションに対する持続ホモロジーを、Lefschetz複体の境界行列に関連する体上で完成させます。

この関数は次の2つの値を返します。

  * `phsingles::Vector{Vector{Int}}`
  * `phpairs::Vector{Vector{Tuple{Int,Int}}}`

フィルトレーション値によって与えられた順序が許容されていると仮定します。すなわち、置換された境界行列は厳密に上三角です。この関数は、`phsingles`における無限長持続区間の開始フィルトレーション値と、`phpairs`における有限長持続区間の出生および死亡フィルトレーション値を返します。
