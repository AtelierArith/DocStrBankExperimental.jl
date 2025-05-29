```Julia
slinch(U::UnitSystem) = mass(𝟏,U,IPS)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²g₀⋅ft⁻¹lb⋅2⋅3 = 1.92248829321(59) × 10³²) [mₑ] Unified
```

英国重力の `slinch` 単位の `mass` (kg または lb)。

```Julia
julia> slinch(Metric) # kg
g₀⋅ft⁻¹lb⋅2²3 = 175.12683524647636 [kg] Metric

julia> slinch(CGS) # g
g₀⋅ft⁻¹lb⋅2⁵3⋅5³ = 175126.83524647637 [g] Gauss

julia> slinch(English) # lb
g₀⋅ft⁻¹2²3 = 386.0885826771653 [lbm] English

julia> slinch(British) # slug
2²3 = 12.0 [slug] British

julia> slinch(Gravitational) # hyl
ft⁻¹lb⋅2²3 = 17.857967322834646 [hyl] Gravitational
```
