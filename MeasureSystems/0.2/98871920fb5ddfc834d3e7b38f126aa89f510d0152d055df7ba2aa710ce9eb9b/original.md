```Julia
katal(U::UnitSystem) = catalysis(𝟏,U,Metric)
catalysis : [T⁻¹N], [T⁻¹N], [T⁻¹N], [T⁻¹N], [T⁻¹N]
T⁻¹N⋅(𝘩⁻¹R∞⁻²α⁴τ⁻¹2⁻⁵5⁻³ = 1.41402394541(87) × 10⁶) [ħ⁻¹𝘤²mₑ²Mᵤ⁻¹ϕ⁻¹g₀⁻¹] Unified
```

Metric unit of `catalysis` (mol⋅s⁻¹ or lb-mol⋅s⁻¹).

```Julia
julia> katal(Metric) # mol⋅s⁻¹
𝟏 = 1.0 [kat] Metric

julia> katal(English) # lb-mol⋅s⁻¹
lb⁻¹2⁻³5⁻³ = 0.002204622621848776 [s⁻¹lb-mol] English

julia> katal(British) # slug-mol⋅s⁻¹
g₀⁻¹ft⋅lb⁻¹2⁻³5⁻³ = 6.852176585679177×10⁻⁵ [s⁻¹slug-mol] British
```
