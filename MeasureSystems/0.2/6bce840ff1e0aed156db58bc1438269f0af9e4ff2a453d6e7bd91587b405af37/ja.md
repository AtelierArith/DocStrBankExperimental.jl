```Julia
radiantintensity : [FLT⁻¹A⁻²], [FLT⁻¹], [ML²T⁻³], [ML²T⁻³], [ML²T⁻³]
radiantintensity(U::UnitSystem,S::UnitSystem) = power(U,S)/solidangle(U,S)
radiantintensity(v::Real,U::UnitSystem,S::UnitSystem) = v/radiantintensity(U,S)
FLT⁻¹A⁻² [ħ⁻¹𝘤⁴mₑ²ϕ⁻³g₀⁻²] 統一

放射強度または `power` を `solidangle` で割ったもの (W⋅sr⁻¹, W⋅rad⁻²)、単位変換係数。

```

Julia julia> radiantintensity(CGS,Metric) # W⋅s⋅erg⁻¹ 2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] ガウス -> メトリック

julia> radiantintensity(English,Metric) # W⋅s⋅ft⁻¹⋅lb⁻¹ g₀⋅ft⋅lb = 1.3558179483314003 [J]/[lbf⋅ft] 英語 -> メトリック ```
