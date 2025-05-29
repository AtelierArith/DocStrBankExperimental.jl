```
cov_to_cor(mat::AbstractMatrix)
```

共分散行列を表す行列を `Hermitian` 相関行列と標準偏差のベクトルに変換します。

### 入力

  * `cor` - 行列。

### 返り値

  * `Hermitian`。
  * 標準偏差の `Vector`（ボラティリティではありません）。
