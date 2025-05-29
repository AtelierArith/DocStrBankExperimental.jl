```Julia
watt(U::UnitSystem) = power(𝟏,U,Metric)
power : [FLT⁻¹], [FLT⁻¹], [ML²T⁻³], [ML²T⁻³], [ML²T⁻³]
FLT⁻¹⋅(𝘩⁻¹𝘤⁻²R∞⁻²α⁴τ⁻¹2⁻² = 1.57331382212(96) × 10⁻⁸) [ħ⁻¹𝘤⁴mₑ²ϕ⁻¹g₀⁻²] Unified
```

Metric `watt` unit of `power` (W or lb⋅ft⋅s⁻¹).

```Julia
julia> watt(Metric) # W
𝟏 = 1.0 [W] Metric

julia> watt(English) # lb⋅ft⋅s⁻¹
g₀⁻¹ft⁻¹lb⁻¹ = 0.7375621492772653 [lbf⋅ft⋅s⁻¹] English

julia> watt(Engineering) # kgf⋅m⋅s⁻¹
g₀⁻¹ = 0.10197162129779283 [kgf⋅m⋅s⁻¹] Engineering
```
