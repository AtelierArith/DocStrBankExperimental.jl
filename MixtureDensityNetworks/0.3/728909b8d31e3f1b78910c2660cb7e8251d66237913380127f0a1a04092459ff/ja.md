```julia
likelihood_loss(
    distributions::Vector{<:Distributions.MixtureModel{Distributions.Univariate}},
    y::Matrix{<:Real}
) -> Any

```

セットの負の対数尤度損失を計算します `y` 単変量ガウス混合モデルのセットの下でのラベル。

# パラメータ

  * `distributions`: 単変量ガウス混合モデル分布のベクトル。
  * `y`: n サンプルの数であるラベルの 1xn 行列。
