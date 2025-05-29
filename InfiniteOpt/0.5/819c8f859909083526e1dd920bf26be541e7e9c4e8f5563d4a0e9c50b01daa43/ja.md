```
JuMP.dual_status(model::InfiniteModel; [result::Int = 1])
```

[`JuMP.dual_status`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.dual_status) を `InfiniteModel` に対して拡張し、最も最近得られた解の結果インデックス `result` に従って、その最適化モデルによって報告されたものに従います。 このようなクエリがサポートされていない場合や、最適化モデルが解決されていない場合はエラーを返します。
