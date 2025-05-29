```
JuMP.objective_bound(model::InfiniteModel)
```

[`JuMP.objective_bound`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.objective_bound) を `InfiniteModel` に対して拡張し、最適化モデルによって報告されたものに従います。このようなクエリがサポートされていない場合や、最適化モデルが解決されていない場合はエラーを返します。
