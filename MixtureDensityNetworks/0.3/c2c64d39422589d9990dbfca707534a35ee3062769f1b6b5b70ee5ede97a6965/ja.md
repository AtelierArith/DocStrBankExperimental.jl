```julia
likelihood_loss(
    distributions::Vector{<:Distributions.MixtureModel{Distributions.Multivariate}},
    y::Matrix{<:Real}
) -> Any

```

多変量ガウス混合モデルのセットに基づいて、ラベル `y` の負の対数尤度損失を計算します。

# パラメータ

  * `distributions`: 多変量ガウス混合モデル分布のベクトル。
  * `y`: 各ラベルの次元が d で、サンプル数が n のラベルの dxn 行列。
