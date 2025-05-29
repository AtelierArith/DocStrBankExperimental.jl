```
LBFGS(model::ScoreDrivenModel, args...; kwargs...)
```

`Int`が提供されると、その数だけランダムな初期点をサンプリングし、それらをOptim LBFGSメソッドの初期点として使用します。`Vector{Vector{T}}`が提供されると、それらをOptim LBFGSメソッドの初期点として使用します。
