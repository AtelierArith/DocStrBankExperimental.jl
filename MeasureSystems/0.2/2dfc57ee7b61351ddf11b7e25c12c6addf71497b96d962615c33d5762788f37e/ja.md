```Julia
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
energy(U::UnitSystem,S::UnitSystem) = mass(U,S)*specificenergy(U,S)
energy(v::Real,U::UnitSystem,S::UnitSystem) = v/energy(U,S)
FL [𝘤²mₑ⋅g₀⁻¹] 統一

作業または熱または `energy` (J, N⋅m, kg⋅m²⋅s⁻²)、単位換算係数。

```

Julia julia> energy(CGS,Metric) # J⋅erg⁻¹ 2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] ガウス -> メトリック

julia> energy(CGS,English) # ft⋅lb⋅erg⁻¹ g₀⁻¹ft⁻¹lb⁻¹2⁻⁷5⁻⁷ = 7.375621492772652×10⁻⁸ [lbf⋅ft]/[erg] ガウス -> 英語

julia> energy(English,Metric) # J⋅ft⁻¹⋅lb⁻¹ g₀⋅ft⋅lb = 1.3558179483314003 [J]/[lbf⋅ft] 英語 -> メトリック

julia> 0.001/3600 # J⋅kW⁻¹⋅h⁻¹ 2.7777777777777776e-7

julia> 1/elementarycharge(SI2019) # J⋅eV⁻¹ 𝘦⁻¹ = 6.241509074460763×10¹⁸ [C⁻¹] SI2019 ```
