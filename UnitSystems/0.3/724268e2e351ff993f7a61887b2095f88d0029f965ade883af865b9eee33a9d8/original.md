```Julia
poise(U::UnitSystem) = viscosity(𝟏,U,Gauss)
```

Metric unit of `viscosity` (kg⋅m⁻¹⋅s⁻¹ or lb⋅s⋅ft⁻²).

```Julia
julia> poise(Metric) # kg⋅m⁻¹⋅s⁻¹
0.09999999999999998

julia> poise(CGS) # g⋅cm⁻¹⋅s⁻¹
1

julia> poise(English) # lb⋅s⋅ft⁻²
0.002088543423315013
```
