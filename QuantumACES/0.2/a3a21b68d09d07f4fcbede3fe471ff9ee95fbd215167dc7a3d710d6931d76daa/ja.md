```
optimise_weights(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; options::OptimOptions = OptimOptions())
```

デザイン `d` と回路の対数固有値推定器共分散行列 `covariance_log` のバージョンを、メリットの指標に関してショットの重みを最適化した後に返します。各ステップでのメリットの指標の値も一緒に返されます。最適化は、特にメリットの指標が計算される最小二乗推定器のタイプを指定する [`OptimOptions`](@ref) オブジェクト `options` によってパラメータ化されています。
