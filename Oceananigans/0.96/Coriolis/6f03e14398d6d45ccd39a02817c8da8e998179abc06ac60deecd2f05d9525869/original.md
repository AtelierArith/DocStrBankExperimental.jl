```
HydrostaticSphericalCoriolis([FT=Float64;]
                             rotation_rate = Ω_Earth,
                             scheme = EnstrophyConserving())
```

Return a parameter object for Coriolis forces on a sphere rotating at `rotation_rate`.

# Keyword arguments

  * `rotation_rate`: Sphere's rotation rate; default: [`Ω_Earth`](@ref).
  * `scheme`: Either `EnergyConserving()`, `EnstrophyConserving()`, or `EnstrophyConserving()` (default).
