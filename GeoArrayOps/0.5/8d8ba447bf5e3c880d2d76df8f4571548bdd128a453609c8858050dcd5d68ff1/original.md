```
multihillshade(dem::Matrix{<:Real}; cellsize=1.0)
```

multihillshade is the simulated illumination of a surface based on its [`slope`](@ref) and [`aspect`](@ref). Like [`hillshade`](@ref), but now using multiple sources as defined in https://pubs.usgs.gov/of/1992/of92-422/of92-422.pdf, similar to GDALs -multidirectional.
