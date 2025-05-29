```julia
function check_collision(a::AbstractShape{2}, b::AbstractShape{2}, state::State{R}) where {R}
```

Given two shapes `a` and `b` and a `state` describing the position and rotation of `b` relative to `a`, return the [`CollisionData`](@ref) describing their separation.
