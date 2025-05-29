```
calc_ls_moments(d::Design; ls_type::Symbol = :gls, est_type::Symbol = :ordinary, est_weight::Float64 = 0.5)
calc_ls_moments(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; ls_type::Symbol = :gls, est_type::Symbol = :ordinary, est_weight::Float64 = 0.5)
```

指定された最小二乗推定量 `ls_type`（`:gls`、`:wls`、または `:ols`）の正規化されたRMS誤差の期待値と分散を返します。これは、設計 `d` に対応し、回路の対数固有値推定器の共分散行列 `covariance_log` を持ち、推定器のタイプ `est_type`（`:ordinary`、`:marginal`、または `:relative`）を持ちます。もし `est_type` が `:sum` または `:prod` に設定されている場合、普通の精度モーメントと相対精度モーメントの算術平均または幾何平均を計算し、`est_weight` によって重み付けされ、普通の精度モーメントに割り当てられます。
