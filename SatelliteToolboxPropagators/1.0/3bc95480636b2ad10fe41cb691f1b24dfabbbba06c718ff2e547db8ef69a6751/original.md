```
twobody_init(orb₀::KeplerianElements; kwargs...) -> TwoBodyPropagator
```

Create and initialize the two-body propagator structure using the mean Keplerian elements `orb₀`.

!!! note
    The type used in the propagation will be the same as used to define the gravitational constant `m0`.


# Keywords

  * `m0::T`: Standard gravitational parameter of the central body [m³ / s²].   (**Default** = `tbc_m0`)
