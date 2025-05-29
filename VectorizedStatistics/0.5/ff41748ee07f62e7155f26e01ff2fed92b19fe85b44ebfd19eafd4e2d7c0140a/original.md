```julia
vminimum(A; dims)
```

Find the least value contained in `A`, optionally over dimensions specified by `dims`. As `Base.minimum`, but vectorized

## Examples

```julia
julia> using VectorizedStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> vminimum(A, dims=1)
1×2 Matrix{Int64}:
 1  2

julia> vminimum(A, dims=2)
 2×1 Matrix{Int64}:
 1
 3
```
