```Julia
圧縮率 : [F⁻¹L²], [F⁻¹L²], [M⁻¹LT²], [M⁻¹LT²], [M⁻¹LT²]
圧縮率(U::UnitSystem,S::UnitSystem) = 1/pressure(U,S)
圧縮率(v::Real,U::UnitSystem,S::UnitSystem) = v/圧縮率(U,S)
F⁻¹L² [ħ³𝘤⁻⁵mₑ⁻⁴ϕ³g₀⁴] 統一

相対体積変化または `圧縮率` (Pa⁻¹)、単位換算係数。

```

Julia julia> 圧縮率(CGS,Metric) # Ba⋅Pa⁻¹ 2⋅5 = 10.0 [Pa⁻¹]/[Ba⁻¹] ガウス -> メトリック

julia> 圧縮率(English,Metric) # lb⋅ft⁻²⋅Pa⁻¹ g₀⁻¹ft²lb⁻¹ = 0.02088543423315013 [Pa⁻¹]/[lbf⁻¹ft²] 英語 -> メトリック

julia> 圧縮率(Metric,IPS) # Pa⋅psi⁻¹ g₀⋅ft⁻²lb⋅2⁴3² = 6894.75729316836 [lb⁻¹in²]/[Pa⁻¹] メトリック -> IPS ```
