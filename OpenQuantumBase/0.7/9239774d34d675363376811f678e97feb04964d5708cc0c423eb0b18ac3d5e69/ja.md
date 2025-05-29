```julia
struct EnsembleFluctuator{T} <: OpenQuantumBase.StochasticBath
```

ランダムテレグラフノイズのアンサンブル。

  * `f`: RTNのリスト
