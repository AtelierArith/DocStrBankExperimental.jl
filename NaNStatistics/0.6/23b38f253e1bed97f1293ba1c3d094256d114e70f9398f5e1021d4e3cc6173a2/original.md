```julia
nanbinmean(x, y, xedges::AbstractRange)
```

Ignoring `NaN`s, calculate the mean of `y` values that fall into each of `length(xedges)-1` equally spaced bins along the `x` axis with bin edges specified by `xedges`.

The array of `x` data should be given as a one-dimensional array (any subtype of AbstractVector) and `y` as either a 1-d or 2-d array (any subtype of AbstractVecOrMat). If `y` is a 2-d array, then each column of `y` will be treated as a separate variable.

## Examples

```julia
julia> nanbinmean([1:100..., 1], [1:100..., NaN], 0:25:100)
4-element Vector{Float64}:
 13.0
 38.0
 63.0
 87.5

julia> nanbinmean(1:100, reshape(1:300,100,3), 0:25:100)
4×3 Matrix{Float64}:
 13.0  113.0  213.0
 38.0  138.0  238.0
 63.0  163.0  263.0
 87.5  187.5  287.5
```
