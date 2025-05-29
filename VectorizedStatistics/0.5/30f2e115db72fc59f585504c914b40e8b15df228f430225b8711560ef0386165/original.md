```julia
vmaximum(A; dims)
```

Find the greatest value contained in `A`, optionally over dimensions specified by `dims`. As `Base.maximum`, but vectorized.

## Examples

```julia
julia> using VectorizedStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> vmaximum(A, dims=1)
1×2 Matrix{Int64}:
 3  4

julia>  vmaximum(A, dims=2)
 2×1 Matrix{Int64}:
 2
 4
```
