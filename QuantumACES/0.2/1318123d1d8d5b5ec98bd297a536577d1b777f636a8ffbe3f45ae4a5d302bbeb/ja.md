```
calc_gate_probabilities_covariance(d::Design; ls_type::Symbol = :gls, est_type::Symbol = :ordinary, unpad::Bool = false)
calc_gate_probabilities_covariance(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; ls_type::Symbol = :gls, est_type::Symbol = :ordinary, unpad::Bool = false)
```

指定された最小二乗推定量 `ls_type`（`:gls`、`:wls`、または `:ols`）に対するパディングされたゲートエラープロバビリティ推定量の共分散行列を返します。これは、回路の対数固有値推定量の共分散行列 `covariance_log` を持つ設計 `d` に対応します。推定量のタイプ `est_type`（`:ordinary`、`:marginal`、または `:relative`）に基づいています。`unpad` が `true` の場合、アイデンティティエラープロバビリティとの共分散が除去された、パディングされていないゲートエラープロバビリティ推定量の共分散行列が返されます。
