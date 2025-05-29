```
calc_ls_covariance(d::Design; ls_type::Symbol = :gls, est_type::Symbol = :ordinary)
calc_ls_covariance(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; ls_type::Symbol = :gls, est_type::Symbol = :ordinary)
```

指定された最小二乗推定量の共分散行列を返します `ls_type` (`:gls`, `:wls`, または `:ols`) は、設計 `d` に対応し、回路の対数固有値推定量の共分散行列 `covariance_log` を持ち、推定量のタイプ `est_type` (`:ordinary`, `:marginal`, または `:relative`) です。
