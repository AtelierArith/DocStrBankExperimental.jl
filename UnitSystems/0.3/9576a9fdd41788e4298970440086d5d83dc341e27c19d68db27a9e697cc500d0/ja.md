```Julia
atmosphere(U::UnitSystem) = pressure(101325.0,U)
```

標準の `pressure` 参照レベルは1気圧 `atm` (Paまたはlb⋅ft⁻²) です。

```Julia
julia> atmosphere(Metric) # Pa
101325.0

julia> atmosphere(English) # lb⋅ft⁻²
2116.2166236739367

julia> atmosphere(IPS) # lb⋅in⁻²
14.695948775513457
```
