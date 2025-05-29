```
CLG = clg(green, redEdge3; kw...)
```

or

```
CLG = clg(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

Green cholorphyl index. Wu et al 2012.

CLG = (redEdge3)/(green)-1 
