```Julia
rayl(U::UnitSystem) = specificimpedance(𝟏,U,Metric)
```

Metric unit of `specificimpedance` (kg⋅m⁻²⋅s⁻¹ or lb⋅s⋅ft⁻³).

```Julia
julia> rayl(Metric) # kg⋅m⁻²⋅s⁻¹
1

julia> rayl(CGS) # g⋅cm⁻²⋅s⁻¹
0.10000000000000003

julia> rayl(English) # lb⋅s⋅ft⁻³
0.00636588035426416
```
