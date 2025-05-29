```
NBRI = nbri(nir, swir3; kw...)
```

or

```
NBRI = nbri(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

Normalised Burn Ratio Index. Garcia 1991

NBRI = (nir - swir2) / (nir + swir2)
