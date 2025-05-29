```
ols_optimise_weights(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; options::OptimOptions = OptimOptions())
```

設計 `d` と回路の対数固有値推定器共分散行列 `covariance_log` のバージョンを、通常最小二乗法 (OLS) の評価基準に関してショットの重みを最適化した後に返します。各ステップでの評価基準の値も返されます。最適化は [`OptimOptions`](@ref) オブジェクト `options` によってパラメータ化されています。
