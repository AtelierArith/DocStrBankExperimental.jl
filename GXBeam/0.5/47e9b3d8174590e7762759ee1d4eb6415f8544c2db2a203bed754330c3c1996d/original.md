```
Assembly{TF, TP<:AbstractVector{<:AbstractVector{TF}},
    TC<:AbstractVector{<:Integer}, TE<:AbstractVector{Element{TF}}}
```

Composite type that defines an assembly of connected nonlinear beam elements.

# Fields

  * `points`: Array of all beam element endpoints
  * `start`: Array containing point index where each beam element starts
  * `stop`: Array containing point index where each beam element stops
  * `elements`: Array containing beam element definitions (see [`Element`](@ref))
