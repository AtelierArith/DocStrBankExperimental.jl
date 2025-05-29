```julia
image_from_paths(tT::TTResult; 
    xresolution::Int=1800, 
    yresolution::Int=1200, 
    xrange = nanextrema(tT.tpointdist), 
    yrange = nanextrema(tT.Tpointdist), 
)
```

Produce a 2d image (histogram) of path densities given a `TTResult`

```julia
julia> imgcounts, xq, yq = image_from_paths(tT; xrange=boundary.agepoints, yrange=boundary.T₀)
```
