```Julia
bar(U::UnitSystem) = pressure(hecto*kilo,U,Metric)
```

圧力の基準単位 (Pa または lb⋅ft⁻²)。

```Julia
julia> bar(Metric) # Pa
100000

julia> bar(English) # lb⋅ft⁻²
2088.5434233150127

julia> bar(IPS) # lb⋅in⁻²
14.50377377302093
```
