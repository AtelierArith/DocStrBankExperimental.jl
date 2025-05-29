```
sparse_covariance_inv(covariance_log::SparseMatrixCSC{Float64, Int}, mapping_lengths::Vector{Int}; epsilon::Real = 1e-12, warning::Bool = true)
```

スパースブロック対角回路のログ固有値推定器共分散行列 `covariance_log` の逆行列を返します。ブロックサイズは `mapping_lengths` によって指定され、コレスキー分解が失敗した場合には最小固有値 `epsilon` を保証し、`warning` が `true` の場合には警告を出します。
