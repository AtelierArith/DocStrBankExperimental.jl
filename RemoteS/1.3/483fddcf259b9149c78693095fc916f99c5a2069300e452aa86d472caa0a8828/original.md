```
CLRE = clre(redEdge1, redEdge3; kw...)
```

or

```
CLRE = clre(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

RedEdge cholorphyl index. Clevers and Gitelson 2013.

CLRE = (redEdge3)/(redEdge1)-1
