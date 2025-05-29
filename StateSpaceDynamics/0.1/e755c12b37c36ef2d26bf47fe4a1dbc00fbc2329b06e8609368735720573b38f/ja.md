```
loglikelihood(model::AutoRegressionEmission, Y_prev::Matrix{<:Real}, Y::Matrix{<:Real})
```

自己回帰エミッションモデルと前の観測値 `Y_prev` に基づいてデータ `Y` の対数尤度を計算します。

# 引数

  * `model::AutoRegressionEmission`: 対数尤度を計算するための自己回帰エミッションモデル。
  * `Y_prev::Matrix{<:Real}`: 各行が観測値を表す前の観測値の行列。
  * `Y::Matrix{<:Real}`: 各行が観測値を表すデータ行列。

# 戻り値

  * `Vector{Float64}`: データ内の各観測値に対する対数尤度のベクトル。
