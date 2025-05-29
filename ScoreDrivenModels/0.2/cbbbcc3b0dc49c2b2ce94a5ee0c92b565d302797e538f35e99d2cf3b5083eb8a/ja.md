```
NelderMead(model::ScoreDrivenModel, args...; kwargs...)
```

`Int`が提供されると、その数だけランダムな初期点をサンプリングし、それらをOptim NelderMeadメソッドの初期点として使用します。`Vector{Vector{T}}`が提供されると、それらをOptim NelderMeadメソッドの初期点として使用します。
