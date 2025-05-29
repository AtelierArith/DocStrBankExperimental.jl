```
acceleration(u::AbstractArray, p::ComponentVector, t::Number, grav_model::GravityHarmonicsAstroModel)
```

Computes the gravitational acceleration acting on a spacecraft given a gravity model and current state and  parameters of an object.

# Arguments

  * `u::AbstractArray`: Current State of the simulation.
  * `p::ComponentVector`: Current parameters of the simulation.
  * `t::Number`: Current time of the simulation.
  * `gravity_model::GravityHarmonicsAstroModel`: Gravity model struct containing the relevant information to compute the acceleration.

# Returns

  * `acceleration: SVector{3}`: The 3-dimensional gravity acceleration acting on the spacecraft.
