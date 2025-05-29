```Julia
specificvolume : [M⁻¹L³], [F⁻¹L⁴T⁻²], [M⁻¹L³], [M⁻¹L³], [M⁻¹L³]
specificvolume(U::UnitSystem,S::UnitSystem) = volume(U,S)/mass(U,S)
specificvolume(v::Real,U::UnitSystem,S::UnitSystem) = v/specificvolume(U,S)
M⁻¹L³ [ħ³𝘤⁻³mₑ⁻⁴ϕ³g₀³] 統一

```

密度の逆数または質量あたりの体積または比体積 (m³⋅kg)、単位換算係数。

```Julia
julia> specificvolume(CGS,Metric) # g⋅m³⋅kg⁻¹⋅cm⁻³
2⁻³5⁻³ = 0.001 [kg⁻¹m³]/[g⁻¹cm³] ガウス -> メトリック

julia> specificvolume(CGS,British) # kg⋅ft³⋅slug⁻¹⋅cm⁻³
g₀⋅ft⁻⁴lb⋅2⁻³5⁻³ = 0.5153788183931961 [lb⁻¹ft⁴s⁻²]/[g⁻¹cm³] ガウス -> ブリティッシュ

julia> specificvolume(English,Metric) # lb⋅m³⋅kg⁻¹⋅ft⁻³
ft³lb⁻¹ = 0.062427960576144616 [kg⁻¹m³]/[lbm⁻¹ft³] 英語 -> メトリック
```
