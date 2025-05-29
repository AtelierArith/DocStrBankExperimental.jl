```Julia
hyl(U::UnitSystem) = mass(𝟏,U,Gravitational)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²g₀⋅2⁻¹ = 1.07654374009(33) × 10³¹) [mₑ] Unified
```

Gravitational Metric `hyl` unit of `mass` (kg or lb).

```Julia
julia> hyl(Metric) # kg
g₀ = 9.80665 [kg] Metric

julia> hyl(CGS) # g
g₀⋅2³5³ = 9806.65 [g] Gauss

julia> hyl(English) # lb
g₀⋅lb⁻¹ = 21.619962434553294 [lbm] English

julia> hyl(British) # slug
ft⋅lb⁻¹ = 0.6719689751395068 [slug] British

julia> hyl(Gravitational) # hyl
𝟏 = 1.0 [hyl] Gravitational
```
