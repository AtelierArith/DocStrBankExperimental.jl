```julia
histcounts(x, xedges::AbstractRange; T=Int64, normalize=false)
```

A 1D histogram, ignoring `NaN`s: calculate the number of `x` values that fall into each of `length(xedges)-1` equally spaced bins along the `x` axis with bin edges specified by `xedges`.

By default, the counts are returned as `Int64`s, though this can be changed by specifying an output type with the optional keyword argument `T`.

## Examples

```julia
julia> b = 10 * rand(100000);

julia> histcounts(b, 0:1:10)
10-element Vector{Int64}:
 10054
  9987
  9851
  9971
  9832
 10033
 10250
 10039
  9950
 10033
```
