```Julia
pound(U::UnitSystem) = mass(𝟏,U,English)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²lb⋅2⁻¹ = 4.9793969039(15) × 10²⁹) [mₑ] Unified
```

English `pound` unit of `mass` (kg or lb).

```Julia
julia> pound(Metric) # kg
lb = 0.45359237 [kg] Metric

julia> pound(CGS) # g
lb⋅2³5³ = 453.59237 [g] Gauss

julia> pound(English) # lb
𝟏 = 1.0 [lbm] English

julia> pound(British) # slug
g₀⁻¹ft = 0.031080950171567256 [slug] British

julia> pound(Gravitational) # hyl
g₀⁻¹lb = 0.046253549377208325 [hyl] Gravitational
```
