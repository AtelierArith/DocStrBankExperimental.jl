```
CLRE = clre(redEdge1, redEdge3; kw...)
```

または

```
CLRE = clre(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

レッドエッジクロロフィル指数。CleversとGitelson 2013。

CLRE = (redEdge3)/(redEdge1)-1
