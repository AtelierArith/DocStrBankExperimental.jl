```Julia
pascal(U::UnitSystem) = pressure(𝟏,U,Metric)
```

Metric unit of `pressure` (Pa or lb⋅ft⁻²).

```Julia
julia> pascal(Metric) # Pa
1

julia> pascal(English) # lb⋅ft⁻²
0.02088543423315013

julia> pascal(IPS) # lb⋅in⁻²
0.0001450377377302093
```
