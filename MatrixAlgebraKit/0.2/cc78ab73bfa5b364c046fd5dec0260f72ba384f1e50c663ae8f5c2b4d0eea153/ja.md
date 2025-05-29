```
svd_vals(A; kwargs...) -> S
svd_vals(A, alg::AbstractAlgorithm) -> S
svd_vals!(A, [S]; kwargs...) -> S
svd_vals!(A, [S], alg::AbstractAlgorithm) -> S
```

行列 `A` の特異値のベクトルを計算します。ここで、M×N 行列 `A` に対して、`S` はサイズ `K = min(M, N)` のベクトルであり、保持される特異値の数です。

また、[`svd_full(!)`](@ref svd_full)、[`svd_compact(!)`](@ref svd_compact)、および [`svd_trunc(!)`](@ref svd_trunc) も参照してください。
