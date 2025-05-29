```
sample(model::GaussianRegressionEmission, Φ::Matrix{<:Real}; n::Int=size(Φ, 1))
```

ガウス回帰モデルから `n` サンプルを生成します。サイズ `(n, output_dim)` の行列を返します。

# 引数

  * `model::GaussianRegressionEmission`: ガウス回帰モデル。
  * `Φ::Matrix{<:Real}`: 形状 `(n, input_dim)` のデザイン行列。
  * `n::Int=size(Φ, 1)`: 生成するサンプルの数。

# 戻り値

  * `Y::Matrix{<:Real}`: 形状 `(n, output_dim)` のサンプルの行列。
