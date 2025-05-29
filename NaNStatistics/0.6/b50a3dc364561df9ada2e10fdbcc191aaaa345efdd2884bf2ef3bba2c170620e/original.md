```julia
nanbinmean(x, y, z, xedges, yedges)
```

Ignoring `NaN`s, calculate the mean of `z` values that fall into a 2D grid of x and y bins with bin edges defined by `xedges` and `yedges`. The independent variables `x` and `y`, as well as the dependent variable `z`, are all expected as 1D vectors (any subtype of AbstractVector).

## Examples

```julia
julia> x = y = z = 0.5:9.5;

julia> xedges = yedges = 0:10;

julia> nanbinmean(x,y,z,xedges,yedges)
10×10 Matrix{Float64}:
   0.5  NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN
 NaN      1.5  NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN
 NaN    NaN      2.5  NaN    NaN    NaN    NaN    NaN    NaN    NaN
 NaN    NaN    NaN      3.5  NaN    NaN    NaN    NaN    NaN    NaN
 NaN    NaN    NaN    NaN      4.5  NaN    NaN    NaN    NaN    NaN
 NaN    NaN    NaN    NaN    NaN      5.5  NaN    NaN    NaN    NaN
 NaN    NaN    NaN    NaN    NaN    NaN      6.5  NaN    NaN    NaN
 NaN    NaN    NaN    NaN    NaN    NaN    NaN      7.5  NaN    NaN
 NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN      8.5  NaN
 NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN      9.5
```
