```julia
image_from_paths(xpoints::AbstractMatrix, ypoints::AbstractMatrix; 
    xresolution::Int=1800, 
    yresolution::Int=1200, 
    xrange=nanextrema(xpoints), 
    yrange=nanextrema(ypoints),
)
```

Produce a 2d image (histogram) of path densities given a set of x-y points  stored column-wise in separate matrices `xpoints` and `ypoints`. `x` is assumed to be the independent variable (i.e., the x-y points are plotted in order of increasing `x`).

### Examples

```julia
julia> nsims = 1000
1000

julia> xdist = rand(10, nsims);

julia> ydist = rand(10, nsims);

julia> imgcounts, xbincenters, ybincenters = image_from_paths(xpaths, ypaths; xresolution=50, yresolution=50)
([8 15 … 9 11; 12 4 … 14 11; … ; 9 15 … 9 9; 10 17 … 10 14], -3.715247394908744:0.1523101612461508:3.747950506152645, -3.86556932981587:0.1497772964483582:3.4735181961536803)
```
