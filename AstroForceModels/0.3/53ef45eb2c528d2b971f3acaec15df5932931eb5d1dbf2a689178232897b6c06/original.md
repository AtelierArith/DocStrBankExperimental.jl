```
acceleration(u::AbstractArray, p::ComponentVector, t::Number, relativity_model::RelativityModel)
```

Computes the srp acceleration acting on a spacecraft given a srp model and current state and  parameters of an object.

# Arguments

  * `u::AbstractArray`: Current State of the simulation.
  * `p::ComponentVector`: Current parameters of the simulation.
  * `t::Number`: Current time of the simulation.
  * `relativity_model::RelativityModel`: Relativity model struct containing the relevant information to compute the acceleration.

# Returns

  * `acceleration: SVector{3}`: The 3-dimensional relativity acceleration acting on the spacecraft.
