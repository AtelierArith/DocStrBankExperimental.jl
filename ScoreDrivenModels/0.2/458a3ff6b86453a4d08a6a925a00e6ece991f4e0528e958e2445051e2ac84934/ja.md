```
IPNewton(model::ScoreDrivenModel, args...; kwargs...)
```

`Int`が提供されると、その数だけランダムな初期点をサンプリングし、それらをOptim IPNewtonメソッドの初期点として使用します。`Vector{Vector{T}}`が提供されると、それらをOptim IPNewtonメソッドの初期点として使用します。

このメソッドはボックス制約を作成するための代替手段を提供します。制約はVectorとして渡すことができ、デフォルトの制約は`ub = Inf * ones(T, dim_unknowns(model))`および`lb = -Inf * ones(T, dim_unknowns(model))`です。
