```Julia
tonne(U::UnitSystem) = mass(𝟏,U,MTS)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²2²5³ = 1.09776910575(34) × 10³³) [mₑ] Unified
```

Metric `tonne` unit of `mass` (kg or lb).

```Julia
julia> tonne(Metric) # kg
2³5³ = 1000.0 [kg] Metric

julia> tonne(MTS) # t
𝟏 = 1.0 [t] MTS

julia> tonne(English) # lb
lb⁻¹2³5³ = 2204.6226218487755 [lbm] English

julia> tonne(British) # slug
g₀⁻¹ft⋅lb⁻¹2³5³ = 68.52176585679176 [slug] British

julia> tonne(Gravitational) # hyl
g₀⁻¹2³5³ = 101.97162129779284 [hyl] Gravitational
```
