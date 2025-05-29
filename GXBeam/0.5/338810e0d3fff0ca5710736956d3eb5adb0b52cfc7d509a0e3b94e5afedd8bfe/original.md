```
Assembly{TF}(points, start, stop, elements)
```

Construct an assembly of connected nonlinear beam elements.  

# Arguments

  * `points`: Array of all beam element endpoints
  * `start`: Array containing point indices where each beam element starts
  * `stop`: Array containing point indices where each beam element stops
  * `elements`: Array containing beam element definitions (see [`Element`](@ref))
