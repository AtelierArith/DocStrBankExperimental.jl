```
JuMP.objective_value(model::InfiniteModel; [result::Int = 1])
```

[`JuMP.objective_value`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.objective_value) を `InfiniteModel` に対して拡張し、最も最近得られた解の結果インデックス `result` に従って、その最適化モデルによって報告された値を返します。サポートされていないクエリや、最適化モデルが解かれていない場合はエラーを返します。
