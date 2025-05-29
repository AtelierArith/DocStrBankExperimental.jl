```
calc_wls_moments(d::Design; est_type::Symbol = :ordinary)
calc_wls_moments(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; est_type::Symbol = :ordinary)
```

設計 `d` に対応する加重最小二乗 (WLS) 推定量の正規化された RMS 誤差の期待値と分散を返します。回路の対数固有値推定器の共分散行列 `covariance_log` と推定器のタイプ `est_type` (`:ordinary`, `:marginal`, または `:relative`) を使用します。
