```
loglikelihood(model::PoissonRegressionEmission, Φ::Matrix{<:Real}, Y::Matrix{<:Real}, w::Vector{Float64}=ones(size(Y, 1)))
```

ポアソン回帰モデルの対数尤度を計算します。

# 引数

  * `model::PoissonRegressionEmission`: ポアソン回帰モデル。
  * `Φ::Matrix{<:Real}`: 形状 `(n, input_dim)` の設計行列。
  * `Y::Matrix{<:Real}`: 形状 `(n, 1)` の応答行列。
  * `w::Vector{Float64}`: データポイントの重み。サイズ `n` のベクトルである必要があります。

# 戻り値

  * `loglikelihood::Float64`: モデルの対数尤度。
