```
de_Sitter_acceleration(
    u::AbstractArray,
    r_sun::AbstractArray,
    v_sun::AbstractArray,
    μ_Sun::Number;
    c::Number=SPEED_OF_LIGHT,
    γ::Number=1.0,
)
```

Computes the relativity acceleration acting on a spacecraft given a relativity model and current state and  parameters of an object.

# Arguments

  * `u::AbstractArray`: Current State of the simulation.
  * `r_sun::AbstractArray`: The position of the sun in the Earth inertial frame.
  * `v_sun::AbstractArray`: The velocity of the sun in the Earth inertial frame.
  * `μ_Sun::Number`: Gravitation Parameter of the Sun. [km^3/s^2]
  * `c::Number`: Speed of Light [km/s]
  * `γ::Number`: Post-Newtonian Parameterization parameter. γ=1 in General Relativity.

# Returns

  * `de_Sitter_acceleration: SVector{3}`: The 3-dimensional de Sitter acceleration acting on the spacecraft.
