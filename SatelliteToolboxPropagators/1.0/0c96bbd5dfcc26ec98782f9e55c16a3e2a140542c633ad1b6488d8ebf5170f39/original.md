```
j2osc_init(orb₀::KeplerianElements; kwargs...) -> J2OsculatingPropagator
```

Create and initialize the J2 osculating orbit propagator structure using the mean Keplerian elements `orb₀` [SI units].

!!! note
    The type used in the propagation will be the same as used to define the constants in the structure `j2c`.


# Keywords

  * `j2c::J2PropagatorConstants`: J2 orbit propagator constants (see   [`J2PropagatorConstants`](@ref)).   (**Default** = `j2c_egm2008`)
