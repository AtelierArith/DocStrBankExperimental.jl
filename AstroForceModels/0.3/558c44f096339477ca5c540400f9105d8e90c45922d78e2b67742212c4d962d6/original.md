```
schwartzchild_acceleration(
    u::AbstractArray, μ_body::Number; c::Number=SPEED_OF_LIGHT, γ::Number=1.0, β::Number=1.0
)
```

Computes the relativity acceleration acting on a spacecraft given a relativity model and current state and  parameters of an object.

# Arguments

  * `u::AbstractArray`: Current State of the simulation.
  * `μ_body::Number`: Gravitation Parameter of the central body.
  * `c::Number`: Speed of Light [km/s]
  * `γ::Number`: Post-Newtonian Parameterization parameter. γ=1 in General Relativity.
  * `β::Number`: Post-Newtonian Parameterization parameter. β=1 in General Relativity.

# Returns

  * `schwartzchild_acceleration: SVector{3}`: The 3-dimensional schwartzchild acceleration acting on the spacecraft.
