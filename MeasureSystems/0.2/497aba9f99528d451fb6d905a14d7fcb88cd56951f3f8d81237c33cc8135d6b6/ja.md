```Julia
horsepowermetric(U::UnitSystem) = power(𝟑*𝟓^2,U,Gravitational)
power : [FLT⁻¹], [FLT⁻¹], [ML²T⁻³], [ML²T⁻³], [ML²T⁻³]
FLT⁻¹⋅(𝘩⁻¹𝘤⁻²R∞⁻²α⁴g₀⋅τ⁻¹2⁻²3⋅5² = 1.15717034952(71) × 10⁻⁵) [ħ⁻¹𝘤⁴mₑ²ϕ⁻¹g₀⁻²] Unified
```

`power`の単位は、1 mを1 sで75 kp上げることから導出されます。

```Julia
julia> horsepowermetric(British) # lb⋅ft⋅s⁻¹
ft⁻¹lb⁻¹3⋅5² = 542.476038840742 [lb⋅ft⋅s⁻¹] British

julia> horsepowermetric(Metric) # W
g₀⋅3⋅5² = 735.49875 [W] Metric

julia> horsepowermetric(Engineering) # kgf⋅m⋅s⁻¹
3⋅5² = 75.0 [kgf⋅m⋅s⁻¹] Engineering
```
