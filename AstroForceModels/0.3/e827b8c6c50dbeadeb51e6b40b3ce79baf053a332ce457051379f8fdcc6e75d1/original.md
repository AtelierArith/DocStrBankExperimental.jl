```
drag_accel(u::AbstractArray, rho::Number, BC::Number, ω_vec::AbstractArray, t::Number, [DragModel]) -> SVector{3}{Number}
```

Compute the Acceleration Atmospheric Drag

The atmosphere is treated as a solid revolving with the Earth and the apparent velocity of the satellite is computed using the transport theorem

```
            𝐯_app = 𝐯 - 𝛚 x 𝐫
```

The acceleration from drag is then computed with a cannonball model as

```
            𝐚 = 1/2 * ρ * BC * |𝐯_app|₂^2 * v̂
```

!!! note
    Currently only fixed cannonball state based ballistic coefficients are supported, custom models can be created for higher fidelity.


# Arguments

  * `u::AbstractArray`: The current state of the spacecraft in the central body's inertial frame.
  * `rho::Number`: Atmospheric density at (t, u) [kg/m^3].
  * `BC::Number`: The ballistic coefficient of the satellite – (area/mass) * drag coefficient [kg/m^2].
  * `ω_vec::AbstractArray`: The angular velocity vector of Earth. Typically approximated as [0.0; 0.0; ω_Earth]
  * `t::Number`: Current time of the simulation.

# Returns

  * `SVector{3}{Number}`: Inertial acceleration from drag
