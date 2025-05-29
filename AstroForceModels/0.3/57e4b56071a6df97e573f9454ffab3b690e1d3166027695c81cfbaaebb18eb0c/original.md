```
srp_accel(u::AbstractArray, sun_pos::AbstractArray, R_Sun::Number, R_Occulting::Number, Ψ::Number, RC::Number, t::Number; ShadowModel::ShadowModelType)
```

Compute the Acceleration from Solar Radiaiton Pressure

Radiation from the Sun reflects off the satellite's surface and transfers momentum perturbing the satellite's trajectory. This force can be computed using the a Cannonball model with the following equation

```
            𝐚 = F * RC * Ψ * (AU/(R_sc_Sun))^2 * R̂_sc_Sun
```

!!! note
    Currently only Cannonball SRP is supported, to use a higher fidelity drag either use a state varying function or compute the ballistic coefficient further upstream


# Arguments

  * `u::AbstractArray`: The current state of the spacecraft in the central body's inertial frame.
  * `sun_pos::AbstractArray`: The current position of the Sun.
  * `R_Sun::Number`: The radius of the Sun.
  * `R_Occulting::Number`: The radius of the Earth.
  * `Ψ::Number`: Solar Constant at 1 Astronomical Unit.
  * `RC::Number`: The solar ballistic coefficient of the satellite – (Area/mass) * Reflectivity Coefficient [kg/m^2].
  * `t::Number`: The current time of the Simulation

# Optional Arguments

  * `ShadowModel::ShadowModelType`: SRP Earth Shadow Model to use. Current Options – :Conical, :Conical_Simplified, :Cylinderical

# Returns

  * `SVector{3}{Number}`: Inertial acceleration from the 3rd body
