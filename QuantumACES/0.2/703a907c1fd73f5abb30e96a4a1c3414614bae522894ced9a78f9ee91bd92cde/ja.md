```
get_relative_gate_covariance(d::Design, gate_eigenvalues_cov::Symmetric{Float64, Matrix{Float64}})
```

デザイン `d` に対応するゲート固有値推定器共分散行列 `gate_eigenvalues_cov` に対する相対ゲート固有値推定器共分散行列を返します。
