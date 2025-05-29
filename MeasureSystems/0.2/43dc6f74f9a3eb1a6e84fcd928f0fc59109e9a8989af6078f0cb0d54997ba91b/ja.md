```Julia
拡散率 : [L²T⁻¹], [L²T⁻¹], [L²T⁻¹], [L²T⁻¹], [L²T⁻¹]
diffusivity(U::UnitSystem,S::UnitSystem) = speed(U,S)*length(U,S)
diffusivity(v::Real,U::UnitSystem,S::UnitSystem) = v/diffusivity(U,S)
L²T⁻¹ [ħ⋅mₑ⁻¹ϕ⋅g₀] 統一

熱的な `diffusivity` または運動粘度 (m²⋅s⁻¹)、単位換算係数。

```

Julia julia> diffusivity(CGS,Metric) # m²⋅cm⁻² 2⁻⁴5⁻⁴ = 0.0001 [m²]/[cm²] ガウス -> メトリック

julia> diffusivity(English,Metric) # m²⋅ft⁻² ft² = 0.09290304 [m²]/[ft²] 英語 -> メトリック

julia> diffusivity(Survey,English) # ft²⋅ftUS⁻² ft⁻²ftUS² = 1.0000040000119996 [ft²]/[ft²] 調査 -> 英語 ```
