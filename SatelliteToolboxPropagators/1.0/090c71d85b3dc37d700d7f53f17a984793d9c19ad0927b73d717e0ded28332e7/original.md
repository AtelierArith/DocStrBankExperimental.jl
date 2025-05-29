```
j2_init!(j2d::J2Propagator, orb₀::KeplerianElements) -> Nothing
```

Initialize the J2 orbit propagator structure `j2d` using the mean Keplerian elements `orb₀` [SI units].

!!! warning
    The propagation constants `j2c::J2PropagatorConstants` in `j2d` will not be changed. Hence, they must be initialized.

