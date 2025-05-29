```julia
vstd(A; dims=:, mean=nothing, corrected=true, multithreaded=false)
```

Compute the variance of all elements in `A`, optionally over dimensions specified by `dims`. As `Statistics.var`, but vectorized and (optionally) multithreaded.

A precomputed `mean` may optionally be provided, which results in a somewhat faster calculation. If `corrected` is `true`, then *Bessel's correction* is applied, such that the sum is divided by `n-1` rather than `n`.

## Examples

```julia
julia> using VectorizedStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> vstd(A, dims=1)
1×2 Matrix{Float64}:
 1.41421  1.41421

julia> vstd(A, dims=2)
2×1 Matrix{Float64}:
 0.7071067811865476
 0.7071067811865476
```
