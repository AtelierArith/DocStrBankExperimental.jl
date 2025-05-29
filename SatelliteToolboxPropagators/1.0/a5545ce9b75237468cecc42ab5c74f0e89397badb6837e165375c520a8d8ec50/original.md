```
j4_init!(j4d::J4Propagator, orb₀::KeplerianElements) -> Nothing
```

Initialize the J4 orbit propagator structure `j4d` using the mean Keplerian elements `orb₀`.

!!! warning
    The propagation constants `j4c::J4PropagatorConstants` in `j4d` will not be changed. Hence, they must be initialized.

