```
gls_optimise_weights(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; options::OptimOptions = OptimOptions())
```

一般化最小二乗法（GLS）の評価基準に関してショットの重みを最適化した後、設計 `d` と回路の対数固有値推定器の共分散行列 `covariance_log` のバージョンを返します。各ステップでの評価基準の値も返されます。最適化は [`OptimOptions`](@ref) オブジェクト `options` によってパラメータ化されています。
