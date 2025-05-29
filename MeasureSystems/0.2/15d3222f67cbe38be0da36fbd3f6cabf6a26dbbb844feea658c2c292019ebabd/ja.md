```Julia
粘度 : [FL⁻²T], [FL⁻²T], [ML⁻¹T⁻¹], [ML⁻¹T⁻¹], [ML⁻¹T⁻¹]
粘度(U::UnitSystem,S::UnitSystem) = 慣性(U,S)/長さ(U,S)/時間(U,S)
粘度(v::Real,U::UnitSystem,S::UnitSystem) = v/粘度(U,S)
FL⁻²T [ħ⁻²𝘤³mₑ³ϕ⁻²g₀⁻³] 統一

変形に対する抵抗または `粘度` (Pa⋅s, kg⋅m⁻¹⋅s⁻¹)、単位換算係数。

```

Julia julia> 粘度(CGS,Metric) # Pa⋅Ba⁻¹ 2⁻¹5⁻¹ = 0.1 [Pa]/[Ba] ガウス -> メトリック

julia> 粘度(English,Metric) # Pa⋅ft²⋅lb⁻¹ g₀⋅ft⁻²lb = 47.88025898033583 [Pa]/[lbf⋅ft⁻²] 英語 -> メトリック

julia> 粘度(British,Metric) # Pa⋅ft²⋅lb⁻¹ g₀⋅ft⁻²lb = 47.88025898033583 [Pa]/[lb⋅ft⁻²] ブリティッシュ -> メトリック ```
