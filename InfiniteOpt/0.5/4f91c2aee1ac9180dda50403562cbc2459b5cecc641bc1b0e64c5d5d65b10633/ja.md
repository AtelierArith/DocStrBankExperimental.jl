```
JuMP.node_count(model::InfiniteModel)
```

[`JuMP.node_count`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.node_count) を `InfiniteModel` に対して拡張し、最適化モデルによって報告されたノード数に従います。このようなクエリがサポートされていない場合や、最適化モデルが解決されていない場合はエラーを返します。
