```Julia
tablespoon(U::UnitSystem) = 𝟑*teaspoon(U)
```

`tablespoon` 単位の `volume` (m³ または ft³) を測定します。

```Julia
julia> tablespoon(Metric) # m³
1.5000000000000002e-5

julia> tablespoon(CGS) # cm³
14.999999999999993

julia> tablespoon(IPS) # in³
0.9153561614209835
```
