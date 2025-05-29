```
NBRI = nbri(nir, swir3; kw...)
```

または

```
NBRI = nbri(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

正規化焼却比指数。ガルシア 1991

NBRI = (nir - swir2) / (nir + swir2)
