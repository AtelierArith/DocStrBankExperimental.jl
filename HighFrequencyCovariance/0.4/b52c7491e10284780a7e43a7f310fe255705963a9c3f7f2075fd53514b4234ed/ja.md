```
cor_to_cov(cor::AbstractMatrix,sdevs::Vector{<:Real})
```

相関行列といくつかの標準偏差を `Hermitian` 共分散行列に変換します。

### 入力

  * `cor` - 相関行列。
  * `sdevs` - 標準偏差のベクトル（ボラティリティではありません）。

### 返り値

  * `Hermitian`。
