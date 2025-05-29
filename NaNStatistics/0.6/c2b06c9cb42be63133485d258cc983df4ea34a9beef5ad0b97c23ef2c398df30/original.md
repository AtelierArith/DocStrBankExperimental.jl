```julia
nanstd(A; dims=:, mean=nothing, corrected=true)
```

Compute the variance of all non-`NaN` elements in `A`, optionally over dimensions specified by `dims`. As `Statistics.var`, but ignoring `NaN`s.

A precomputed `mean` may optionally be provided, which results in a somewhat faster calculation. If `corrected` is `true`, then *Bessel's correction* is applied, such that the sum is divided by `n-1` rather than `n`.

As an alternative to `dims`, `nanstd` also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).

## Examples

```julia
julia> using NaNStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nanstd(A, dims=1)
1×2 Matrix{Float64}:
 1.41421  1.41421

julia> nanstd(A, dims=2)
2×1 Matrix{Float64}:
 0.7071067811865476
 0.7071067811865476
```
