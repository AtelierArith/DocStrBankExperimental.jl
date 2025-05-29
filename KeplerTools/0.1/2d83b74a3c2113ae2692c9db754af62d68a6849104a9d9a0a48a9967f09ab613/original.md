```
r̄, v̄ = state_vector(θ, a, e, μ, basis)
r̄, v̄ = state_vector(θ, a, e, μ, i, Ω, ω)
r̄, v̄ = state_vector(θ, orbit)
```

Compute the state vector at true anomaly `θ` of an orbit with with semimajor axis `a`,  eccentricity `e`, gravity paremter `μ`, and a rotation `basis` defining the orbit's perifocal plane.

The rotation can be computed from inclinaion `i`, RAAN `Ω`, and the argument of the periapsis `ω`.
