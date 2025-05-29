```Julia
照度 : [FL⁻¹T⁻¹], [FL⁻¹T⁻¹], [MT⁻³], [MT⁻³], [MT⁻³]
照度(U::UnitSystem,S::UnitSystem) = power(U,S)/area(U,S)
照度(v::Real,U::UnitSystem,S::UnitSystem) = v/照度(U,S)
FL⁻¹T⁻¹ [ħ⁻³𝘤⁶mₑ⁴ϕ⁻³g₀⁻⁴] 統一

```

熱流密度または照度または `power` あたりの `area` (W⋅m⁻², kg⋅s⁻³)、単位変換係数。

```Julia
julia> 照度(CGS,Metric) # kg⋅g⁻¹
2⁻³5⁻³ = 0.001 [N⋅m⁻¹]/[dyn⋅cm⁻¹] ガウス -> メトリック

julia> 照度(CGS,English) # lb⋅g⁻¹
g₀⁻¹ft⋅lb⁻¹2⁻³5⁻³ = 6.852176585679177×10⁻⁵ [lbf⋅ft⁻¹]/[dyn⋅cm⁻¹] ガウス -> 英語

julia> 照度(English,Metric) # kg⋅lb⁻¹
g₀⋅ft⁻¹lb = 14.593902937206364 [N⋅m⁻¹]/[lbf⋅ft⁻¹] 英語 -> メトリック
```
