```
construct_matrix_from_eigen(
    eigenvalues::Vector{<:Real},
    eigenvectors::Matrix{<:Real},
)
```

固有値分解から行列を構築します。

### 入力

  * `eigenvalues` - 固有値のベクトル。
  * `eigenvectors` - 固有ベクトルの行列。i番目の列はi番目の固有値に対応します。

### 戻り値

  * `Matrix`。
