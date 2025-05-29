```
loglikelihood(model::BernoulliRegressionEmission, Φ::Matrix{<:Real}, Y::Matrix{<:Real}, w::Vector{Float64}=ones(size(Y, 1)))
```

データ `Y` の対数尤度を、ベルヌーイ回帰発生モデルと入力特徴 `Φ` に基づいて計算します。オプションで、重みのベクトル `w` を提供することができます。

# 引数

  * `model::BernoulliRegressionEmission`: 対数尤度を計算するためのベルヌーイ回帰発生モデル。
  * `Φ::Matrix{<:Real}`: 入力特徴行列（観測 x 特徴）。
  * `Y::Matrix{<:Real}`: データ行列（観測 x 特徴）。
  * `w::Vector{Float64}`: 各観測に対応する重みのベクトル（デフォルトは1のベクトル）。

# 戻り値

  * `Vector{Float64}`: データ内の各観測に対する対数尤度のベクトル。
