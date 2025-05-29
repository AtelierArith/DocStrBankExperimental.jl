```Julia
kmh(U::UnitSystem) = kilo(U)*meter(U)/hour(U)
```

時速キロメートルの単位 `speed` (m⋅s⁻¹ または ft⋅s⁻¹)。

```Julia
julia> kmh(Metric) # m⋅s⁻¹
0.2777777777777778

julia> kmh(MPH) # mi⋅h⁻¹
0.621371192237334

julia> kmh(Nautical) # nm⋅h⁻¹
0.5392191813436995
```
