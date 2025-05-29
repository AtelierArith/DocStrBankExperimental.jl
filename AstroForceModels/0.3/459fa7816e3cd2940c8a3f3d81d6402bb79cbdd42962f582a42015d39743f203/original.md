```
acceleration(u::AbstractArray, p::ComponentVector, t::Number, drag_model::DragAstroModel)
```

Computes the drag acceleration acting on a spacecraft given a drag model and current state and  parameters of an object.

# Arguments

  * `u::AbstractArray`: Current State of the simulation.
  * `p::ComponentVector`: Current parameters of the simulation.
  * `t::Number`: Current time of the simulation.
  * `drag_model::DragAstroModel`: Drag model struct containing the relevant information to compute the acceleration.

# Returns

  * `acceleration: SVector{3}`: The 3-dimensional drag acceleration acting on the spacecraft.
