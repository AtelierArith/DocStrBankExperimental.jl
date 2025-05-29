```julia
nanbinmedian(x, y, xedges::AbstractRange)
```

Calculate the median, ignoring `NaN`s, of y values that fall into each of `length(xedges)-1` equally spaced bins along the `x` axis with bin edges specified by `xedges`.

If `y` is a 2-d array (matrix), each column will be treated as a separate variable

## Examples

```julia
julia> nanbinmedian([1:100..., 1], [1:100..., NaN], 0:25:100)
4-element Vector{Float64}:
 12.5
 37.0
 62.0
 87.0

julia> nanbinmedian(1:100, reshape(1:300,100,3), 0:25:100)
4×3 Matrix{Float64}:
 12.5  112.5  212.5
 37.0  137.0  237.0
 62.0  162.0  262.0
 87.0  187.0  287.0
```
