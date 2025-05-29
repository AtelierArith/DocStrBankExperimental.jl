```Julia
apm(U::UnitSystem) = 𝟏/minute(U)
```

Actions per minute `apm` unit of `frequency` (s⁻¹).

```Julia
julia> apm(Metric) # s⁻¹
0.016666666666666666

julia> apm(MPH) # h⁻¹
60.000000000000014

julia> apm(IAU) # D⁻¹
1440.0000000000002
```
