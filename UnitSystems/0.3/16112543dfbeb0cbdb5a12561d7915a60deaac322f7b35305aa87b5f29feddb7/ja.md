```Julia
teaspoon(U::UnitSystem) = 𝟓*milli*liter(U)
```

`teaspoon` 単位の `volume` (m³ または ft³) を測定します。

```Julia
julia> teaspoon(Metric) # m³
5.0e-6

julia> teaspoon(CGS) # cm³
4.999999999999997

julia> teaspoon(IPS) # in³
0.3051187204736612
```
