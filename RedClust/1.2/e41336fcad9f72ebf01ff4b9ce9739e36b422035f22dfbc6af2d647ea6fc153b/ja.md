```
sampleK(params::PriorHyperparamsList, numsamples::Int, n::Int)::Vector{Int}
sampleK(η::Real, σ::Real, u::Real, v::Real, numsamples::Int, n::Int)
```

`params`から推定された周辺事前予測分布から生成された$K$（クラスタの数）のサンプルを含む長さ`numsamples`のベクトルを返します。パラメータ`n`はモデル内の観測数です。
