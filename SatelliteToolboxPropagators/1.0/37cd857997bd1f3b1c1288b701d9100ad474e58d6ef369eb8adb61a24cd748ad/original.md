```
j2osc_init!(j2oscd::J2OsculatingPropagator, orb₀::KeplerianElements) -> Nothing
```

Initialize the J2 osculating orbit propagator structure `j2oscd` using the mean Keplerian elements `orb₀` [SI units].

!!! warning
    The propagation constants `j2c::J2PropagatorConstants` in `j2oscd.j2d` will not be changed. Hence, they must be initialized.

