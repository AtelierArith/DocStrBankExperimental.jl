```
loglikelihood(model::GaussianEmission, Y::Matrix{<:Real})
```

ガウス排出モデルに基づいてデータ `Y` の対数尤度を計算します。

# 引数

  * `model::GaussianEmission`: 対数尤度を計算するためのガウス排出モデル。
  * `Y::Matrix{<:Real}`: 各行が観測を表すデータ行列。

# 戻り値

  * `Vector{Float64}`: データ内の各観測に対する対数尤度のベクトル。
