```julia
nanmean(A; dims)
```

Compute the mean of all non-`NaN` elements in `A`, optionally over dimensions specified by `dims`. As `Statistics.mean`, but ignoring `NaN`s.

As an alternative to `dims`, `nanmean` also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).

## Examples

```julia
julia> using NaNStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nanmean(A, dims=1)
1×2 Matrix{Float64}:
 2.0  3.0

julia> nanmean(A, dims=2)
2×1 Matrix{Float64}:
 1.5
 3.5
```
