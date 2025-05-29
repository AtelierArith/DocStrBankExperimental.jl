```
JuMP.solve_time(model::InfiniteModel)
```

[`JuMP.solve_time`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.solve_time) を `InfiniteModel` に対して拡張し、その最適化モデルによって報告された時間に従います。このようなクエリがサポートされていない場合や、最適化モデルが解かれていない場合はエラーを返します。
