```
loglikelihood(model::GaussianRegressionEmission, Φ::Matrix{<:Real}, Y::Matrix{<:Real})
```

ガウス回帰エミッションモデルと入力特徴 `Φ` に基づいて、データ `Y` の対数尤度を計算します。

# 引数

  * `model::GaussianRegressionEmission`: 対数尤度を計算するためのガウス回帰エミッションモデル。
  * `Φ::Matrix{<:Real}`: 入力特徴行列（観測 x 特徴）。
  * `Y::Matrix{<:Real}`: データ行列（観測 x 特徴）。

# 戻り値

  * `Vector{Float64}`: データ内の各観測に対する対数尤度のベクトル。
