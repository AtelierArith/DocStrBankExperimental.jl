```
calc_gls_covariance(d::Design)
calc_gls_covariance(d::Design, covariance_log::SparseMatrixCSC{Float64, Int})
```

設計 `d` に対応する一般化最小二乗 (GLS) 推定量のゲート固有値推定器共分散行列を、回路ログ固有値推定器共分散行列 `covariance_log` と共に返します。
