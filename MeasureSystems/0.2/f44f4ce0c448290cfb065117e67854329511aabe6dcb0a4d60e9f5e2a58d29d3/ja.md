```Julia
specificenergy : [FM⁻¹L], [L²T⁻²], [L²T⁻²], [L²T⁻²], [L²T⁻²]
specificenergy(U::UnitSystem,S::UnitSystem) = speed(U,S)^2/gravity(U,S)
specificenergy(v::Real,U::UnitSystem,S::UnitSystem) = v/specificenergy(U,S)
FM⁻¹L [𝘤²g₀⁻¹] 統一

質量あたりのエネルギーまたは `mass` あたりの `energy` または `specificenergy` (J⋅kg⁻¹)、単位換算係数。

```

Julia julia> specificenergy(CGS,Metric) # m²⋅cm⁻² 2⁻⁴5⁻⁴ = 0.0001 [J⋅kg⁻¹]/[erg⋅g⁻¹] ガウス -> メトリック

julia> specificenergy(IAU,Metric) # m²⋅day²⋅s⁻²⋅au⁻² au²2⁻¹⁴3⁻⁶5⁻⁴ = 2.99794277772(12) × 10¹² [J⋅kg⁻¹]/[au²D⁻²] IAU☉ -> メトリック

julia> specificenergy(English,Metric) # m²⋅ft⁻² g₀⋅ft = 2.98906692 [J⋅kg⁻¹]/[lbf⋅lbm⁻¹ft] 英語 -> メトリック

julia> specificenergy(Survey,English) # ft²⋅ftUS⁻² ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] 調査 -> 英語 ```
