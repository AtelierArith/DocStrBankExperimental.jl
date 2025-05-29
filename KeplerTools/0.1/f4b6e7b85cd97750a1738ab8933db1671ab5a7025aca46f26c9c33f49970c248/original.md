```
r̄ = orbital_position(θ, a, e, basis)
r̄ = orbital_position(θ, a, e, i, Ω, ω)
r̄ = orbital_position(θ, orbit)
```

Compute the position vector at true anomaly `θ` of an orbit with with semimajor axis `a`,  eccentricity `e`, and a rotation `basis` defining the orbit's perifocal plane.

The rotation can be computed from inclinaion `i`, RAAN `Ω`, and the argument of the periapsis `ω`.
