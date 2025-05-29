```julia
histcounts(x, y, xedges::AbstractRange, yedges::AbstractRange; T=Int64, normalize=false)
```

A 2D histogram, ignoring `NaN`s: calculate the number of `x, y` pairs that fall into each square of a 2D grid of equally-spaced square bins with edges specified by `xedges` and `yedges`.

The resulting matrix `N` of counts is oriented with the lowest x and y bins in `N[1,1]`, where the first (vertical / row) dimension of `N` corresponds to the y axis (with `size(N,1) == length(yedges)-1`) and the second (horizontal / column) dimension of `N` corresponds to the x axis (with `size(N,2) == length(xedges)-1`).

By default, the counts are returned as `Int64`s, though this can be changed by specifying an output type with the optional keyword argument `T`.

## Examples

```julia
julia> x = y = 0.5:9.5;

julia> xedges = yedges = 0:10;

julia> N = histcounts(x,y,xedges,yedges)
10×10 Matrix{Int64}:
 1  0  0  0  0  0  0  0  0  0
 0  1  0  0  0  0  0  0  0  0
 0  0  1  0  0  0  0  0  0  0
 0  0  0  1  0  0  0  0  0  0
 0  0  0  0  1  0  0  0  0  0
 0  0  0  0  0  1  0  0  0  0
 0  0  0  0  0  0  1  0  0  0
 0  0  0  0  0  0  0  1  0  0
 0  0  0  0  0  0  0  0  1  0
 0  0  0  0  0  0  0  0  0  1
```
