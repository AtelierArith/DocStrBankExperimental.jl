```Julia
powerdensity : [FL⁻²T⁻¹], [FL⁻²T⁻¹], [ML⁻¹T⁻³], [ML⁻¹T⁻³], [ML⁻¹T⁻³]
powerdensity(U::UnitSystem,S::UnitSystem) = power(U,S)/volume(U,S)
powerdensity(v::Real,U::UnitSystem,S::UnitSystem) = v/powerdensity(U,S)
FL⁻²T⁻¹ [ħ⁻⁴𝘤⁷mₑ⁵ϕ⁻⁴g₀⁻⁵] 統一

スペクトル放射照度（体積）または `powerdensity` (W⋅m⁻³)、単位換算係数。

```

Julia julia> powerdensity(CGS,Metric) # kg⋅cm⋅g⁻¹⋅m⁻¹ 2⁻¹5⁻¹ = 0.1 [Pa]/[Ba] ガウス -> メトリック

julia> powerdensity(CGS,English) # lb⋅cm⋅g⁻¹⋅ft⁻¹ g₀⁻¹ft²lb⁻¹2⁻¹5⁻¹ = 0.002088543423315013 [lbf⋅ft⁻²]/[Ba] ガウス -> 英語

julia> powerdensity(English,Metric) # kg⋅ft⋅lb⁻¹⋅m⁻¹ g₀⋅ft⁻²lb = 47.88025898033583 [Pa]/[lbf⋅ft⁻²] 英語 -> メトリック ```
