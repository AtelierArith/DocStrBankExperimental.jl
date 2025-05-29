```Julia
tonsrefrigeration(U::UnitSystem) = frequency(𝟐*𝟓/𝟑,U,Metric)*thermalunit(U)
power : [FLT⁻¹], [FLT⁻¹], [ML²T⁻³], [ML²T⁻³], [ML²T⁻³]
FLT⁻¹⋅(𝘩⁻¹𝘤⁻²R∞⁻²α⁴lb⋅Ωᵢₜ⁻¹Vᵢₜ²τ⁻¹2⁴3⁻¹5⁶43⁻¹ = 5.5330303556(34) × 10⁻⁵) [ħ⁻¹𝘤⁴mₑ²ϕ⁻¹g₀⁻²] Unified
```

Unit of `power` derived from melting of 1 short ton of ice in 24 hours.

```Julia
julia> tonsrefrigeration(British) # lb⋅ft⋅s⁻¹
g₀⁻¹ft⁻¹Ωᵢₜ⁻¹Vᵢₜ²2⁶3⁻¹5⁶43⁻¹ = 2593.8587099969172 [lb⋅ft⋅s⁻¹] British

julia> tonsrefrigeration(Metric) # W
lb⋅Ωᵢₜ⁻¹Vᵢₜ²2⁶3⁻¹5⁶43⁻¹ = 3516.8001944495536 [W] Metric

julia> tonsrefrigeration(Engineering) # kgf⋅m⋅s⁻¹
g₀⁻¹lb⋅Ωᵢₜ⁻¹Vᵢₜ²2⁶3⁻¹5⁶43⁻¹ = 358.613817608414 [kgf⋅m⋅s⁻¹] Engineering
```
