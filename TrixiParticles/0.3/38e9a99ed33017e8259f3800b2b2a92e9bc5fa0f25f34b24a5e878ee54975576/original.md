```
BoundaryMovement(movement_function, is_moving; moving_particles=nothing)
```

# Arguments

  * `movement_function`: Time-dependent function returning an `SVector` of $d$ dimensions                      for a $d$-dimensional problem.
  * `is_moving`: Function to determine in each timestep if the particles are moving or not. Its   boolean return value is mandatory to determine if the neighborhood search will be updated.

# Keyword Arguments

  * `moving_particles`: Indices of moving particles. Default is each particle in [`BoundarySPHSystem`](@ref).

In the example below, `movement` describes particles moving in a circle as long as the time is lower than `1.5`.

# Examples

```jldoctest; output = false
movement_function(t) = SVector(cos(2pi*t), sin(2pi*t))
is_moving(t) = t < 1.5

movement = BoundaryMovement(movement_function, is_moving)

# output
BoundaryMovement{typeof(movement_function), typeof(is_moving), Vector{Int64}}(movement_function, is_moving, Int64[])
```
