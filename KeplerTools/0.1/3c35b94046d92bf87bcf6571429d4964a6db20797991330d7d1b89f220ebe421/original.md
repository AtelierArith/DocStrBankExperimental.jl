```
v̄ = orbital_velocity(θ, a, e, μ, basis)
v̄ = orbital_velocity(θ, a, e, μ, i, Ω, ω)
v̄ = orbital_velocity(θ, orbit)
```

Compute the velocity vector at true anomaly `θ` of an orbit with with semimajor axis `a`,  eccentricity `e`, gravity paremter `μ`, and a rotation `basis` defining the orbit's perifocal plane.

The rotation can be computed from inclinaion `i`, RAAN `Ω`, and the argument of the periapsis `ω`.
