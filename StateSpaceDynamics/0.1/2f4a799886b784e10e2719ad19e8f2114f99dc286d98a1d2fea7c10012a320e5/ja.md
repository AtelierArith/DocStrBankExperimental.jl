```
sample(model::PoissonRegressionEmission, Φ::Matrix{<:Real}; n::Int=size(Φ, 1))
```

ポアソン回帰モデルから `n` サンプルを生成します。サイズ `(n, 1)` の行列を返します。

# 引数

  * `model::PoissonRegressionEmission`: ポアソン回帰モデル。
  * `Φ::Matrix{<:Real}`: 形状 `(n, input_dim)` のデザイン行列。
  * `n::Int=size(Φ, 1)`: 生成するサンプルの数。

# 返り値

  * `Y::Matrix{<:Real}`: 形状 `(n, 1)` のサンプルの行列。
