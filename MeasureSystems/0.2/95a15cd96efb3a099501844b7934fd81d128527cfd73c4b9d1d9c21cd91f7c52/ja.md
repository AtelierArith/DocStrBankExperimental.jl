```Julia
horsepower(U::UnitSystem) = power(𝟐*𝟓^2*𝟏𝟏,U,British)
power : [FLT⁻¹], [FLT⁻¹], [ML²T⁻³], [ML²T⁻³], [ML²T⁻³]
FLT⁻¹⋅(𝘩⁻¹𝘤⁻²R∞⁻²α⁴g₀⋅ft⋅lb⋅τ⁻¹2⁻¹5²11 = 1.17321991511(72) × 10⁻⁵) [ħ⁻¹𝘤⁴mₑ²ϕ⁻¹g₀⁻²] Unified
```

`power`の単位は、1秒間に1フィートの高さで550ポンドを持ち上げることから導出されます。

```Julia
julia> horsepower(British) # lb⋅ft⋅s⁻¹
2⋅5²11 = 550.0 [lb⋅ft⋅s⁻¹] British

julia> horsepower(Metric) # W
g₀⋅ft⋅lb⋅2⋅5²11 = 745.6998715822701 [W] Metric

julia> horsepower(Engineering) # kgf⋅m⋅s⁻¹
ft⋅lb⋅2⋅5²11 = 76.0402249068 [kgf⋅m⋅s⁻¹] Engineering
```
