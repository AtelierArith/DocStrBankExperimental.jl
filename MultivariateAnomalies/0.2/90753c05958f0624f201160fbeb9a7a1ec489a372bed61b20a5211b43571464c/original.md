```
kernel_matrix(D::AbstractArray, σ::Float64 = 1.0[, kernel::String = "gauss", dimension::Int64 = 1])
```

compute a kernel matrix out of distance matrix `D`, given `σ`. Optionally normalized by the `dimension`, if `kernel = "normalized_gauss"`. compute `D` with `dist_matrix()`.

# Examples

```
julia> dc = randn(20, 4,3)
julia> D = dist_matrix(dc, space = 2)
julia> K = kernel_matrix(D, 2.0)
```
