```
hillshade(dem::Matrix{<:Real}; azimuth=315.0, zenith=45.0, cellsize=1.0)
```

hillshade is the simulated illumination of a surface based on its [`slope`](@ref) and [`aspect`](@ref) given a light source with azimuth and zenith angles in °, , as defined in Burrough, P. A., and McDonell, R. A., (1998, Principles of Geographical Information Systems).
