```
solve_mc_fault_study(case::Dict{String,<:Any}, solver; kwargs...)
```

データセット `case` と最適化 `solver` を考慮して多導体（配電）故障研究を解決する関数

`kwargs` は PowerModelsDistribution の `solve_mc_model` に対する有効なキーワード引数であれば何でも使用できます。
