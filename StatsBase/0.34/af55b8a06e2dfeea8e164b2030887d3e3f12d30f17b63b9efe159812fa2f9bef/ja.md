```
cov(ce::CovarianceEstimator, X::AbstractMatrix, [w::AbstractWeights];
    mean=nothing, dims::Int=1)
```

行列 `X` の共分散行列を、推定器 `ce` を使用して次元 `dims` に沿って計算します。重みベクトル `w` を指定することができます。キーワード引数 `mean` は次のように指定できます：

  * `nothing`（デフォルト）の場合、平均が推定され、データ `X` から引かれます。
  * 事前に計算された平均の場合、データ `X` から引かれます。`size(X)` が `(N,M)` の場合、`mean` は次のいずれかになります：

      * `dims=1` の場合、サイズ `(1,M)` の `AbstractMatrix`、
      * `dims=2` の場合、長さ `N` の `AbstractVector` またはサイズ `(N,1)` の `AbstractMatrix`。
