```Julia
atmosphere(U::UnitSystem) = pressure(101325.0,U)
```

Standard `pressure` reference level of one atmosphere `atm` (Pa or lb⋅ft⁻²).

```Julia
julia> atmosphere(Metric) # Pa
101325.0

julia> atmosphere(English) # lb⋅ft⁻²
2116.2166236739367

julia> atmosphere(IPS) # lb⋅in⁻²
14.695948775513457
```
