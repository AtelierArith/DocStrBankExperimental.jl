```
calc_wls_covariance(d::Design)
calc_wls_covariance(d::Design, covariance_log::SparseMatrixCSC{Float64, Int})
```

設計 `d` に対応する加重最小二乗 (WLS) 推定量のゲート固有値推定器共分散行列を、回路ログ固有値推定器共分散行列 `covariance_log` と共に返します。
