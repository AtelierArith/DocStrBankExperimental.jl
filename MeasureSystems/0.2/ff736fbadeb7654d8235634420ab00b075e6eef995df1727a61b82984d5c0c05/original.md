```Julia
ton(U::UnitSystem) = mass(𝟐*kilo,U,English)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²lb⋅2³5³ = 9.9587938078(31) × 10³²) [mₑ] Unified
```

English `ton` unit of `mass` (kg or lb).

```Julia
julia> ton(Metric) # kg
lb⋅2⁴5³ = 907.18474 [kg] Metric

julia> ton(MTS) # t
lb⋅2 = 0.90718474 [t] MTS

julia> ton(English) # lb
2⁴5³ = 2000.0 [lbm] English

julia> ton(British) # slug
g₀⁻¹ft⋅2⁴5³ = 62.16190034313451 [slug] British

julia> ton(Gravitational) # hyl
g₀⁻¹lb⋅2⁴5³ = 92.50709875441665 [hyl] Gravitational
```
