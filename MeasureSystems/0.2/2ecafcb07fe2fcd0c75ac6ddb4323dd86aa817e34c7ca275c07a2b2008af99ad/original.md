```Julia
boilerhorsepower(U::UnitSystem) = frequency(1339/𝟐^4/𝟑^2,U,Metric)*thermalunit(U)
power : [FLT⁻¹], [FLT⁻¹], [ML²T⁻³], [ML²T⁻³], [ML²T⁻³]
FLT⁻¹⋅1339 [ħ⁻¹𝘤⁴mₑ²ϕ⁻¹g₀⁻²] Unified
```

Unit of `power` derived from evaporating 34.5 lb of boiling water in 1 hour.

```Julia
julia> boilerhorsepower(British) # lb⋅ft⋅s⁻¹
g₀⁻¹ft⁻¹Ωᵢₜ⁻¹Vᵢₜ²2⋅3⁻²5⁵43⁻¹⋅1339 = 7235.785026428902 [lb⋅ft⋅s⁻¹] British

julia> boilerhorsepower(Metric) # W
lb⋅Ωᵢₜ⁻¹Vᵢₜ²2⋅3⁻²5⁵43⁻¹⋅1339 = 9810.407209099902 [W] Metric

julia> boilerhorsepower(Engineering) # kgf⋅m⋅s⁻¹
g₀⁻¹lb⋅Ωᵢₜ⁻¹Vᵢₜ²2⋅3⁻²5⁵43⁻¹⋅1339 = 1000.3831287034718 [kgf⋅m⋅s⁻¹] Engineering
```
