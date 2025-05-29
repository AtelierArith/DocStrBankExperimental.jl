```
reflection_coef(θ, ρᵣ, cᵣ, δ=0.0)
```

Compute complex reflection coefficient at a fluid-fluid boundary, given:

  * angle of incidence `θ` (angle to the surface normal)
  * relative density of the reflecting medium to incidence medium `ρᵣ`
  * relative sound speed of the reflecting medium to incidence medium `cᵣ`
  * dimensionless absorption coefficient `δ`

Implementation based on Brekhovskikh & Lysanov. Dimensionless absorption coefficient based on APL-UW Technical Report 9407.
