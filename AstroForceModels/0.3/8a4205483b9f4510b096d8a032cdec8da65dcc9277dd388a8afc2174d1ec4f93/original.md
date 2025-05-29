```
lense_thirring_acceleration(
    u::AbstractArray,
    μ_body::Number,
    J::AbstractArray;
    c::Number=SPEED_OF_LIGHT,
    γ::Number=1.0,
)
```

Computes the lense thirring relativity acceleration acting on a spacecraft given a relativity model and current state and  parameters of an object.

# Arguments

  * `u::AbstractArray`: Current State of the simulation.
  * `μ_body::Number`: Gravitation Parameter of the central body.
  * `J::AbstractArray`: Angular momentum vector per unit mass of the central body. [km^3/s^2]
  * `c::Number`: Speed of Light [km/s]
  * `γ::Number`: Post-Newtonian Parameterization parameter. γ=1 in General Relativity.

# Returns

  * `lense_thirring_acceleration: SVector{3}`: The 3-dimensional lense thirring acceleration acting on the spacecraft.
