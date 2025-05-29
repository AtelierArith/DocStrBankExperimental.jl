```
j4(Δt::Number, orb₀::KeplerianElements; kwargs...) -> SVector{3, T}, SVector{3, T}, J4Propagator
```

Initialize the J4 propagator structure using the input elements `orb₀` and propagate the orbit until the time Δt [s].

!!! note
    The type used in the propagation will be the same as used to define the constants in the structure `j4c`.


# Keywords

  * `j4c::J4PropagatorConstants`: J4 orbit propagator constants (see   [`J4PropagatorConstants`](@ref)).   (**Default** = `j4c_egm2008`)

# Returns

  * `SVector{3, T}`: Position vector [m] represented in the inertial frame at propagation   instant.
  * `SVector{3, T}`: Velocity vector [m / s] represented in the inertial frame at propagation   instant.
  * [`J4Propagator`](@ref): Structure with the initialized parameters.

# Remarks

The inertial frame in which the output is represented depends on which frame it was used to generate the orbit parameters. Notice that the perturbation theory requires an inertial frame with true equator.
