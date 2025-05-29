```
acceleration(u::AbstractArray, p::ComponentVector, t::Number, srp_model::SRPAstroModel)
```

Computes the srp acceleration acting on a spacecraft given a srp model and current state and  parameters of an object.

# Arguments

  * `u::AbstractArray`: Current State of the simulation.
  * `p::ComponentVector`: Current parameters of the simulation.
  * `t::Number`: Current time of the simulation.
  * `srp_model::SRPAstroModel`: SRP model struct containing the relevant information to compute the acceleration.

# Returns

  * `acceleration: SVector{3}`: The 3-dimensional srp acceleration acting on the spacecraft.
