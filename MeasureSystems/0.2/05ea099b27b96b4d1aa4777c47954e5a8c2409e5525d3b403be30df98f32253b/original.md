```Julia
electricalhorsepower(U::UnitSystem) = power(746,U,Metric)
power : [FLT⁻¹], [FLT⁻¹], [ML²T⁻³], [ML²T⁻³], [ML²T⁻³]
FLT⁻¹⋅373 [ħ⁻¹𝘤⁴mₑ²ϕ⁻¹g₀⁻²] Unified
```

Unit of `power` for electrical motors in the United States.

```Julia
julia> electricalhorsepower(British) # lb⋅ft⋅s⁻¹
g₀⁻¹ft⁻¹lb⁻¹2⋅373 = 550.2213633608399 [lb⋅ft⋅s⁻¹] British

julia> electricalhorsepower(Metric) # W
2⋅373 = 746.0 [W] Metric

julia> electricalhorsepower(Engineering) # kgf⋅m⋅s⁻¹
g₀⁻¹2⋅373 = 76.07082948815345 [kgf⋅m⋅s⁻¹] Engineering
```
