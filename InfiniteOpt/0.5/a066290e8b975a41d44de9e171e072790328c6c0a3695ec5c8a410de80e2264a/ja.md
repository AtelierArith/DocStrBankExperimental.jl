```
JuMP.termination_status(model::InfiniteModel)
```

[`JuMP.termination_status`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.termination_status) を `InfiniteModel` に対して拡張し、その最適化モデルによって報告された内容に従います。サポートされていないクエリを行った場合や、最適化モデルが解かれていない場合はエラーを返します。
