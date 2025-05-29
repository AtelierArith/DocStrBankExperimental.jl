```julia
histcountindices(x, xedges::AbstractRange; T=Int64)
```

A 1D histogram, ignoring `NaN`s; as `histcounts` but also returning a vector of the bin index of each `x` value.

## Examples

```julia
julia> b = 10 * rand(100000);

julia> N, bin = histcountindices(b, 0:2:10)
([20082, 19971, 20049, 19908, 19990], [2, 3, 2, 2, 4, 2, 3, 3, 2, 4  …  1, 3, 3, 3, 3, 5, 2, 3, 3, 1])
```
