```Julia
molarenergy : [FLN⁻¹], [FLN⁻¹], [ML²T⁻²N⁻¹], [ML²T⁻²N⁻¹], [ML²T⁻²N⁻¹]
molarenergy(U::UnitSystem,S::UnitSystem) = energy(U,S)/molaramount(U,S)
molarenergy(v::Real,U::UnitSystem,S::UnitSystem) = v/molarenergy(U,S)
FLN⁻¹ [𝘤²Mᵤ⋅g₀⁻¹] 統一

ギブス自由 `エネルギー` あたり `モル` または `molarenergy` (J⋅mol⁻¹)、単位変換係数。

```

Julia julia> molarenergy(CGS,Metric) # J⋅erg⁻¹ 2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] ガウス -> メトリック

julia> molarenergy(English,SI2019) # J⋅slug-mol⋅ft⁻¹⋅lb⁻¹⋅mol⁻¹ NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⋅ft⋅2 = 0.00298906691897(92) [J⋅mol⁻¹]/[lbf⋅ft⋅lb-mol⁻¹] 英語 -> SI2019 ```
