```Julia
horsepowerwatt(U::UnitSystem) = power(𝟐^4*𝟑^3/𝟓*τ,U,British)
power : [FLT⁻¹], [FLT⁻¹], [ML²T⁻³], [ML²T⁻³], [ML²T⁻³]
FLT⁻¹⋅(𝘩⁻¹𝘤⁻²R∞⁻²α⁴g₀⋅ft⋅lb⋅2²3³5⁻¹ = 1.15800476849(71) × 10⁻⁵) [ħ⁻¹𝘤⁴mₑ²ϕ⁻¹g₀⁻²] Unified
```

`power`の単位はワットの正確な元の馬力推定から導出されています。

```Julia
julia> horsepowerwatt(British) # lb⋅ft⋅s⁻¹
τ⋅2⁴3³5⁻¹ = 542.8672105403163 [lb⋅ft⋅s⁻¹] British

julia> horsepowerwatt(Metric) # W
g₀⋅ft⋅lb⋅τ⋅2⁴3³5⁻¹ = 736.0291076111621 [W] Metric

julia> horsepowerwatt(Engineering) # kgf⋅m⋅s⁻¹
ft⋅lb⋅τ⋅2⁴3³5⁻¹ = 75.05408142547782 [kgf⋅m⋅s⁻¹] Engineering
```
