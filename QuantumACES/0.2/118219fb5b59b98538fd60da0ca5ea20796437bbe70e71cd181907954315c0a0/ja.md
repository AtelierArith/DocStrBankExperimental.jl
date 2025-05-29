```
wls_optimise_weights(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; options::OptimOptions = OptimOptions())
```

デザイン `d` と回路の対数固有値推定器共分散行列 `covariance_log` のバージョンを、加重最小二乗 (WLS) のメリットに関してショットウェイトを最適化した後に返します。各ステップでのメリット値も一緒に返されます。最適化は [`OptimOptions`](@ref) オブジェクト `options` によってパラメータ化されています。
