```
relativity_accel(
    u::AbstractArray,
    r_sun::AbstractArray,
    v_sun::AbstractArray,
    μ_body::Number,
    μ_Sun::Number,
    J::AbstractArray;
    c::Number=SPEED_OF_LIGHT / 1E3,
    γ::Number=1.0,
    β::Number=1.0,
    schwartzchild_effect::Bool=true,
    lense_thirring_effect::Bool=true,
    de_Sitter_effect::Bool=true,
)
```

Computes the relativity acceleration acting on a spacecraft given a relativity model and current state and  parameters of an object.

# Arguments

  * `u::AbstractArray`: Current State of the simulation.
  * `r_sun::AbstractArray`: The position of the sun in the Earth inertial frame.
  * `v_sun::AbstractArray`: The velocity of the sun in the Earth inertial frame.
  * `μ_body::Number`: Gravitation Parameter of the central body.
  * `μ_Sun::Number`: Gravitation Parameter of the Sun. [km^3/s^2]
  * `J::AbstractArray`: Angular momentum vector per unit mass of the central body. [km^3/s^2]
  * `c::Number`: Speed of Light [km/s]
  * `γ::Number`: Post-Newtonian Parameterization parameter. γ=1 in General Relativity.
  * `β::Number`: Post-Newtonian Parameterization parameter. β=1 in General Relativity.
  * `schwartzchild_effect::Bool`: Include the Schwartzchild relativity effect.
  * `lense_thirring_effect::Bool`: Include the Lense Thirring relativity effect.
  * `de_Sitter_effect::Bool`: Include the De Sitter relativity effect.

# Returns

  * `acceleration: SVector{3}`: The 3-dimensional relativity acceleration acting on the spacecraft.
