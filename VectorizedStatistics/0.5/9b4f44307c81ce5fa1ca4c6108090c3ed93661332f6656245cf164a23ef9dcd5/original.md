```julia
vmean(A; dims, multithreaded=false)
```

Compute the mean of all elements in `A`, optionally over dimensions specified by `dims`. As `Statistics.mean`, but vectorized and (optionally) multithreaded.

## Examples

```julia
julia> using VectorizedStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> vmean(A, dims=1)
1×2 Matrix{Float64}:
 2.0  3.0

julia> vmean(A, dims=2)
2×1 Matrix{Float64}:
 1.5
 3.5
```
