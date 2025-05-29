```
kernel_matrix!(K, D::AbstractArray, σ::Float64 = 1.0[, kernel::String = "gauss", dimension::Int64 = 1])
```

compute a kernel matrix out of distance matrix `D`. Similar to `kernel_matrix()`, but with preallocated Array K (`K = similar(D)`) for output.

# Examples

```
julia> dc = randn(20, 4,3)
julia> D = dist_matrix(dc, space = 2)
julia> kernel_matrix!(D, D, 2.0) # overwrites distance matrix
```
