```Julia
specificweight : [FL⁻³], [FL⁻³], [ML⁻²T⁻²], [ML⁻²T⁻²], [ML⁻²T⁻²]
specificweight(U::UnitSystem,S::UnitSystem) = force(U,S)/volume(U,S)
specificweight(v::Real,U::UnitSystem,S::UnitSystem) = v/specificweight(U,S)
FL⁻³ [ħ⁻⁴𝘤⁶mₑ⁵ϕ⁻⁴g₀⁻⁵] 統一

特定重量または `体積` あたりの `力` (N⋅m⁻³ または lb⋅ft⁻³)、単位換算係数。

```

Julia julia> specificweight(CGS,Metric) # N⋅cm³⋅dyn⁻¹⋅m⁻³ 2⋅5 = 10.0 [kg⋅m⁻²s⁻²]/[g⋅cm⁻²s⁻²] ガウス -> メトリック

julia> specificweight(CGS,Brtish) # lb⋅cm³⋅dyn⁻¹⋅ft⁻³ g₀⁻¹ft³lb⁻¹2⋅5 = 0.0636588035426416 [lb⋅ft⁻³]/[g⋅cm⁻²s⁻²] ガウス -> ブリティッシュ

julia> specificweight(English,Metric) # N⋅ft³⋅lb⁻¹⋅m⁻³ g₀⋅ft⁻³lb = 157.08746384624618 [kg⋅m⁻²s⁻²]/[lbf⋅ft⁻³] 英語 -> メトリック ```
