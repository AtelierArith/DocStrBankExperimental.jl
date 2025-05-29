```
cov(estimator::WoodburyEstimator, X::AbstractMatrix, weights::FrequencyWeights...; dims::Int=1, mean=nothing, UsV=nothing)
```

データ行列 `X` から「スパイク」共分散モデルを使用して共分散行列を推定します。

```
Σ = σ²I + U * Λ * U',
```

ここで `U` は固有ベクトルの低ランク行列であり、`Λ` は対角行列です。

参考文献: Donoho, D.L., Gavish, M. and Johnstone, I.M., 2018. スパイク共分散モデルにおける固有値の最適な縮小. Annals of statistics, 46(4), p.1742.

`σ²` が `estimator` に供給されていない場合、残差 `X - X̂` から計算されます。ここで `X̂` は `U` と `Λ` を生成するために使用される `X` の低ランク近似です。

`X` がメモリ内で操作するには大きすぎる場合、`UsV = (U, s, V)`（`X - mean(X; dims)` の切り捨てられた SVD）を渡すことができ、その場合 `X` は次元数と観測数を計算するためにのみ使用されます。これには `estimator.σ²` を指定する必要があります。
