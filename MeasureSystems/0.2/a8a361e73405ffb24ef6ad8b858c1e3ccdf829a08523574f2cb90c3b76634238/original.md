```Julia
grain(U::UnitSystem) = milli(U)*pound(U)/𝟕
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²lb⋅2⁻⁴5⁻³7⁻¹ = 7.1134241484(22) × 10²⁵) [mₑ] Unified
```

Ideal `grain` seed of cereal, unit of `mass` (kg or lb).

```Julia
julia> grain(Metric) # kg
lb⋅2⁻³5⁻³7⁻¹ = 6.479891×10⁻⁵ [kg] Metric

julia> grain(CGS) # g
lb⋅7⁻¹ = 0.06479891 [g] Gauss

julia> grain(English) # lb
2⁻³5⁻³7⁻¹ = 0.00014285714285714284 [lbm] English

julia> grain(QCD) # mₚ
𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹lb⋅2⁻⁴5⁻³7⁻¹ = 3.8740918723(12) × 10²² [mₚ] QCD
```
