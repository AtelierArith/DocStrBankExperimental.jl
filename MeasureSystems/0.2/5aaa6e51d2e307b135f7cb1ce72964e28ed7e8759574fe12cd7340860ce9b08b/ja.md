```Julia
kilogram(U::UnitSystem) = mass(𝟏,U,Metric)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²2⁻¹ = 1.09776910575(34) × 10³⁰) [mₑ] Unified
```

Metric `kilogram` unit of `mass` (kg or lb).

```Julia
julia> kilogram(Metric) # kg
𝟏 = 1.0 [kg] Metric

julia> kilogram(CGS) # g
2³5³ = 1000.0 [g] Gauss

julia> kilogram(English) # lb
lb⁻¹ = 2.2046226218487757 [lbm] English

julia> kilogram(British) # slug
g₀⁻¹ft⋅lb⁻¹ = 0.06852176585679176 [slug] British

julia> kilogram(Gravitational) # hyl
g₀⁻¹ = 0.10197162129779283 [hyl] Gravitational
```
