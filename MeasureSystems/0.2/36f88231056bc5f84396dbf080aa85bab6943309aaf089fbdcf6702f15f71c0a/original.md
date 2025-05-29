```Julia
ounce(U::UnitSystem) = pound(U)/𝟐^4
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²lb⋅2⁻⁵ = 3.11212306494(95) × 10²⁸) [mₑ] Unified
```

English `ounce` unit of `mass` (kg or lb).

```Julia
julia> ounce(Metric) # kg
lb⋅2⁻⁴ = 0.028349523125 [kg] Metric

julia> ounce(CGS) # g
lb⋅2⁻¹5³ = 28.349523125 [g] Gauss

julia> ounce(English) # lb
2⁻⁴ = 0.0625 [lbm] English

julia> ounce(British) # slug
g₀⁻¹ft⋅2⁻⁴ = 0.0019425593857229535 [slug] British

julia> ounce(Gravitational) # hyl
g₀⁻¹lb⋅2⁻⁴ = 0.0028908468360755203 [hyl] Gravitational
```
