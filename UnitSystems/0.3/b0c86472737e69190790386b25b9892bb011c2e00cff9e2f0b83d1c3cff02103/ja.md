```Julia
roentgen(U::UnitSystem) = chargedensity(𝟏,U,ESU)/density(Constant(1.293),U,Metric)
```

イオン化のレガシー単位 `exposure` (C⋅kg⁻¹ または C⋅lb⁻¹)。

```Julia
julia> roentgen(Metric) # C⋅kg⁻¹
0.0002579768717696457

julia> roentgen(English) # C⋅lb⁻¹
0.00011701634067117976
```
