```
j2(Δt::Number, orb₀::KeplerianElements; kwargs...) -> SVector{3, T}, SVector{3, T}, J2Propagator
```

Initialize the J2 propagator structure using the input elements `orb₀` [SI units] and propagate the orbit until the time Δt [s].

!!! note
    The type used in the propagation will be the same as used to define the constants in the structure `j2c`.


# Keywords

  * `j2c::J2PropagatorConstants`: J2 orbit propagator constants (see   [`J2PropagatorConstants`](@ref)).   (**Default** = `j2c_egm2008`)

# Returns

  * `SVector{3, T}`: Position vector [m] represented in the inertial frame at propagation   instant.
  * `SVector{3, T}`: Velocity vector [m / s] represented in the inertial frame at propagation   instant.
  * [`J2Propagator`](@ref): Structure with the initialized parameters.

# Remarks

The inertial frame in which the output is represented depends on which frame it was used to generate the orbit parameters. Notice that the perturbation theory requires an inertial frame with true equator.
