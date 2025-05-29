```Julia
specificforce : [FM⁻¹], [LT⁻²], [LT⁻²], [LT⁻²], [LT⁻²]
specificforce(U::UnitSystem,S::UnitSystem) = acceleration(U,S)/gravity(U,S)
specificforce(v::Real,U::UnitSystem,S::UnitSystem) = v/specificforce(U,S)
FM⁻¹ [ħ⁻¹𝘤³mₑ⋅ϕ⁻¹g₀⁻²] 統一

質量あたりの重さまたは `force` または `gforce` (N/kg, m⋅s⁻²)、単位変換係数。

```

Julia julia> specificforce(CGS,Metric) 2⁻²5⁻² = 0.010000000000000002 [m⋅s⁻²]/[gal] ガウス -> メトリック

julia> specificforce(Engineering,Metric) g₀ = 9.80665 [N]/[kgf] エンジニアリング -> メトリック

julia> specificforce(English,Metric) g₀ = 9.80665 [m⋅s⁻²]/[g₀] 英語 -> メトリック ```
