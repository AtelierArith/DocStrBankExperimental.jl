```
StateVectorSimulator{T, S<:AbstractVector{T}} <: AbstractSimulator
```

状態ベクトルのタイプ `S` と要素タイプ `T` の純粋状態進化を表すシミュレーター。状態ベクトルシミュレーターは、ノイズのない回路をシミュレートするために使用されるべきです。
