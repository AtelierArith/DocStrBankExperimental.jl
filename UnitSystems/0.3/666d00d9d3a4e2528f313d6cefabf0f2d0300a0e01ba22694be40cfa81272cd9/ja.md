```Julia
langley(U::UnitSystem) = calorie(U)/(centi*meter(U))^2
```

太陽放射単位 (kg⋅s⁻² または lb⋅ft⁻¹)。

```Julia
julia> langley(Metric) # kg⋅s⁻²
41867.37323211057

julia> langley(CGS) # g⋅s⁻²
4.186737323211057e7

julia> langley(English) # lb⋅ft⁻¹
2868.8263456495906
```
