```Julia
放射輝度 : [FL⁻¹T⁻¹A⁻²], [FL⁻¹T⁻¹], [MT⁻³], [MT⁻³], [MT⁻³]
放射輝度(U::UnitSystem,S::UnitSystem) = 照度(U,S)/固体角(U,S)
放射輝度(v::Real,U::UnitSystem,S::UnitSystem) = v/放射輝度(U,S)
FL⁻¹T⁻¹A⁻² [ħ⁻³𝘤⁶mₑ⁴ϕ⁻⁵g₀⁻⁴] 統一

```

放射輝度または `照度` あたり `固体角` (W⋅m⁻²⋅sr⁻¹, kg⋅s⁻³⋅sr⁻¹)、単位換算係数。

```Julia
julia> 放射輝度(CGS,Metric) # kg⋅g⁻¹
2⁻³5⁻³ = 0.001 [N⋅m⁻¹]/[dyn⋅cm⁻¹] ガウス -> メトリック

julia> 放射輝度(CGS,English) # lb⋅g⁻¹
g₀⁻¹ft⋅lb⁻¹2⁻³5⁻³ = 6.852176585679177×10⁻⁵ [lbf⋅ft⁻¹]/[dyn⋅cm⁻¹] ガウス -> 英語

julia> 放射輝度(English,Metric) # kg⋅lb⁻¹
g₀⋅ft⁻¹lb = 14.593902937206364 [N⋅m⁻¹]/[lbf⋅ft⁻¹] 英語 -> メトリック
```
