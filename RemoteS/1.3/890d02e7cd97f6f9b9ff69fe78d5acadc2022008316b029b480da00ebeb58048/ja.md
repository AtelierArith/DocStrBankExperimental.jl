```
NDREI2 = ndrei2(redEdge1, redEdge3; kw...)
```

または

```
NDREI2 = ndrei2(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

正規化差分赤端指数2。Barnes et al 2000

NDREI2 = (redEdge3 - redEdge1) / (redEdge3 + redEdge1)
