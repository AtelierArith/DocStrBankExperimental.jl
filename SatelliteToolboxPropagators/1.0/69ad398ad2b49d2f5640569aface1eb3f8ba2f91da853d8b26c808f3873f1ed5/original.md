```
j4osc_init!(j4oscd::J4OsculatingPropagator, orb₀::KeplerianElements) -> Nothing
```

Initialize the J4 osculating orbit propagator structure `j4oscd` using the mean Keplerian elements `orb₀`.

!!! warning
    The propagation constants `j4c::J4PropagatorConstants` in `j4oscd.j4d` will not be changed. Hence, they must be initialized.

