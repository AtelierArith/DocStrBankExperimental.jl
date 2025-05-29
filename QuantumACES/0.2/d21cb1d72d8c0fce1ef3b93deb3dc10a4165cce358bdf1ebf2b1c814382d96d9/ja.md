```
optimise_tuple_set(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; options::OptimOptions = OptimOptions())
```

デザイン `d` と回路の対数固有値推定器共分散行列 `covariance_log` のバージョンを返します。これは、タプルセットを成長させたり剪定したりする反復的な探検を通じてデザインのタプルセットを最適化した後のものです。最適化は [`OptimOptions`](@ref) オブジェクト `options` によってパラメータ化されています。
