```
twobody(Δt::Number, orb₀::KeplerianElements; kwargs...) -> SVector{3, T}, SVector{3, T}, TwoBodyPropagator
```

Initialize the two-body propagator structure using the input elements `orb₀` and propagate the orbit until the time Δt [s].

!!! note
    The type used in the propagation will be the same as used to define the gravitational constant `m0`.


# Keywords

  * `m0::T`: Standard gravitational parameter of the central body [m³ / s²].   (**Default** = `tbc_m0`)

# Returns

  * `SVector{3, T}`: Position vector [m] represented in the inertial frame at propagation   instant.
  * `SVector{3, T}`: Velocity vector [m / s] represented in the inertial frame at propagation   instant.
  * [`TwoBodyPropagator`](@ref): Structure with the initialized parameters.

# Remarks

The inertial frame in which the output is represented depends on which frame it was used to generate the orbit parameters.
