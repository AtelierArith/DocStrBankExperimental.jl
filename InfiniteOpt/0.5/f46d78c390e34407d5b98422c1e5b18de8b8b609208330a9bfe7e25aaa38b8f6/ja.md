```
JuMP.dual_objective_value(model::InfiniteModel; [result::Int = 1])
```

[`JuMP.dual_objective_value`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.dual_objective_value) を `InfiniteModel` に対して拡張し、最適化モデルによって報告された値と、取得した最新の解の結果インデックス `result` に従います。 このようなクエリがサポートされていない場合や、最適化モデルが解決されていない場合はエラーを返します。
