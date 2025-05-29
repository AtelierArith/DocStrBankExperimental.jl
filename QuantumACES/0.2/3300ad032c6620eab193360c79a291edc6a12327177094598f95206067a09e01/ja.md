```
calc_covariance_log(covariance::SparseMatrixCSC{Float64, Int}, eigenvalues::Vector{Float64})
calc_covariance_log(d::Design; warning::Bool = true)
```

回路の固有値 `eigenvalues` に対応する回路の対数固有値の共分散行列を、共分散行列 `covariance` を使用して、設計 `d` から生成された値を用いて返します。また、`warning` が `true` の場合、`d.full_covariance` が `false` の場合は、共分散行列の対角成分のみが生成されることを警告します。
