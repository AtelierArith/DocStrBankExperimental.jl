```
JuMP.has_values(model::InfiniteModel; [result::Int = 1])
```

[`JuMP.has_values`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.has_values) を `InfiniteModel` に対して拡張し、最も最近取得した解の結果インデックス `result` に従って、その最適化モデルによって報告された内容に従います。 そのようなクエリがサポートされていない場合や、最適化モデルが解決されていない場合はエラーを返します。
