```Julia
teaspoon(U::UnitSystem) = 𝟓*milli*liter(U)
```

Measuring `teaspoon` unit of `volume` (m³ or ft³).

```Julia
julia> teaspoon(Metric) # m³
5.0e-6

julia> teaspoon(CGS) # cm³
4.999999999999997

julia> teaspoon(IPS) # in³
0.3051187204736612
```
