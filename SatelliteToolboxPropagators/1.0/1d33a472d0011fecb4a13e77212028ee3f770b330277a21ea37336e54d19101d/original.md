```
twobody_init!(tbd::TwoBodyPropagator, orb₀::KeplerianElements; kwargs...) -> Nothing
```

Initialize the two-body propagator structure `tbd` using the mean Keplerian elements `orb₀`.

!!! warning
    The propagation constant `μ::Number` in `tbd` will not be changed. Hence, it must be initialized.

