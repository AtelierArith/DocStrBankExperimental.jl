```julia
likelihood_loss(
    distributions::Vector{<:Distributions.MixtureModel{Distributions.Univariate}},
    y::Matrix{<:Real}
) -> Any

```

与えられた一連のラベル `y` に対して、単変量ガウス混合モデルのセットの下で負の対数尤度損失を計算します。

# パラメータ

  * `distributions`: 単変量ガウス混合モデル分布のベクトル。
  * `y`: n がサンプルの数であるラベルの1xn行列。
