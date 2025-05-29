```julia
vsum(A; dims, multithreaded=false)
```

Summate the values contained in `A`, optionally over dimensions specified by `dims`. As `Base.sum`, but vectorized and (optionally) multithreaded.

## Examples

```julia
julia> using VectorizedStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> vsum(A, dims=1)
1×2 Matrix{Int64}:
 4  6

julia> vsum(A, dims=2)
2×1 Matrix{Int64}:
 3
 7
```
