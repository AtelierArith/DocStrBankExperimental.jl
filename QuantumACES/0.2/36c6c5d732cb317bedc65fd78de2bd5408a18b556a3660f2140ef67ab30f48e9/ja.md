```
calc_ols_covariance(d::Design)
calc_ols_covariance(d::Design, covariance_log::SparseMatrixCSC{Float64, Int})
```

設計 `d` に対応する通常最小二乗 (OLS) 推定量のゲート固有値推定器共分散行列を、回路ログ固有値推定器共分散行列 `covariance_log` と共に返します。
