```
j4_init(orb₀::KeplerianElements; kwargs...) -> J4Propagator
```

Create and initialize the J4 orbit propagator structure using the mean Keplerian elements `orb₀`.

!!! note
    The type used in the propagation will be the same as used to define the constants in the structure `j4c`.


# Keywords

  * `j4c::J4PropagatorConstants`: J4 orbit propagator constants (see   [`J4PropagatorConstants`](@ref)).   (**Default** = `j4c_egm2008`)
