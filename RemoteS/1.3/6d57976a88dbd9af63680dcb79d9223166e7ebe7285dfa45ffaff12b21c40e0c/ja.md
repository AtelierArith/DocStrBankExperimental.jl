```
CLG = clg(green, redEdge3; kw...)
```

または

```
CLG = clg(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

グリーン葉緑素指数。Wu et al 2012。

CLG = (redEdge3)/(green)-1 
