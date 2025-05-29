```
stabilize_covariance_matrix(Σ::Matrix{<:Real})
```

共分散行列を安定化させるために、対称かつ正定値であることを保証します。

# 引数

  * `Σ::Matrix{<:Real}`: 入力の共分散行列。

# 戻り値

  * 入力の共分散行列の安定化されたバージョン。
