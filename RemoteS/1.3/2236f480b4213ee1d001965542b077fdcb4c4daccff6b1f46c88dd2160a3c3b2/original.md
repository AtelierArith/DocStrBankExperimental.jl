```
SATVI = satvi(red, swir2, swir3; kw...)
```

or

```
SATVI = satvi(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

Soil adjusted total vegetation index. Marsett 2006

SATVI = ((swir1 - red) / (swir1 + red + L)) * (1.0 + L) - (swir2 / 2.0)
