```
fit!(model::GaussianEmission, Y::Matrix{<:Real}, w::Vector{Float64}=ones(size(Y, 1)))
```

データ `Y` にガウスエミッションモデルをフィットします。

# 引数

  * `model::GaussianEmission`: フィットするガウスモデル。
  * `Y::Matrix{<:Real}`: モデルにフィットさせるデータ。サイズは `(n, output_dim)` の行列である必要があります。
  * `w::Vector{Float64}=ones(size(Y, 1))`: データの重み。サイズは `n` のベクトルである必要があります。
