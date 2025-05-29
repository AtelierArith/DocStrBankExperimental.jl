```
NDREI2 = ndrei2(redEdge1, redEdge3; kw...)
```

or

```
NDREI2 = ndrei2(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

Normalized difference red edge index 2. Barnes et al 2000

NDREI2 = (redEdge3 - redEdge1) / (redEdge3 + redEdge1)
