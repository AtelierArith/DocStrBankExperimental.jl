```julia
nansum(A; dims)
```

Calculate the sum of an indexable collection `A`, ignoring `NaN`s, optionally along dimensions specified by `dims`.

Also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).

## Examples

```julia
julia> using NaNStatistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nansum(A, dims=1)
1×2 Matrix{Int64}:
 4  6

julia> nansum(A, dims=2)
2×1 Matrix{Int64}:
 3
 7
```
