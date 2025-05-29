```
calc_gls_moments(d::Design; est_type::Symbol = :ordinary)
calc_gls_moments(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; est_type::Symbol = :ordinary)
```

一般化最小二乗法（GLS）推定量に対応する設計 `d` の正規化されたRMS誤差の期待値と分散を返します。回路の対数固有値推定器の共分散行列 `covariance_log` と推定器のタイプ `est_type`（`:ordinary`、`:marginal`、または `:relative`）を使用します。
