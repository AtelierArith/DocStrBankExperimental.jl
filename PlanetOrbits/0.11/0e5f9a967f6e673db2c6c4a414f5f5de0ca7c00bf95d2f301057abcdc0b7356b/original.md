```
KepOrbit(
    a, # semi-major axis [AU]
    e, # eccentricity
    i, # inclination [rad]
    ω, # argument of periapsis [rad]
    Ω, # longitude of ascending node [rad]
    tp, # epoch of periastron passage at MJD=0
    M, # mass of primary [M⊙]
)
```

Represents the Keplerian elements of a secondary body orbiting a primary. Use the traditional Campbell parameterization. Values can be specified by keyword argument or named tuple for convenience.
