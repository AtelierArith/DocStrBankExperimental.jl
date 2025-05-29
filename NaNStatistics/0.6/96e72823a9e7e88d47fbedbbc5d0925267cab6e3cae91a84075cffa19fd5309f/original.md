```julia
nansem(A; dims=:, mean=nothing, corrected=true)
```

Compute the standard error of the mean of all non-`NaN` elements in `A`, optionally  over dimensions specified by `dims`.

A precomputed `mean` may optionally be provided, which results in a somewhat faster calculation. If `corrected` is `true`, then *Bessel's correction* is applied, such that the sum is divided by `n-1` rather than `n`.

As an alternative to `dims`, `nansem` also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).

## Examples

```julia
julia> using NaNStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nansem(A, dims=1)
1×2 Matrix{Float64}:
 2.0  2.0

julia> nansem(A, dims=2)
2×1 Matrix{Float64}:
 0.5
 0.5
```
