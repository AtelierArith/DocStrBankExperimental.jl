```julia
nanskewness(A; dims=:, mean=nothing)
```

Compute the skewness of all non-`NaN` elements in `A`, optionally over dimensions specified by `dims`. As `StatsBase.skewness`, but ignoring `NaN`s.

A precomputed `mean` may optionally be provided, which results in a somewhat faster calculation.

As an alternative to `dims`, `nanskewness` also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).

## Examples

```julia
julia> using NaNStatistics

julia> A = [1 2 3 ; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> nanskewness(A, dims=1)
1×3 Matrix{Float64}:
 0.0  0.0  0.0


julia> nanskewness(A, dims=2)
3-element Vector{Float64}:
 0.0
 0.0
 0.0
```
