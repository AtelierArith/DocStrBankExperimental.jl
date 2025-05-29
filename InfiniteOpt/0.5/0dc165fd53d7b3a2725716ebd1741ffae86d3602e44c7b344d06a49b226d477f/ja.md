```
JuMP.has_duals(model::InfiniteModel; [result::Int = 1])
```

[`JuMP.has_duals`](https://jump.dev/JuMP.jl/v0.22/reference/solutions/#JuMP.has_duals) を `InfiniteModel` に対して拡張し、最も最近取得した解の結果インデックス `result` に従って、その最適化モデルによって報告された内容に従います。 そのようなクエリがサポートされていない場合や、最適化モデルが解決されていない場合はエラーが発生します。
