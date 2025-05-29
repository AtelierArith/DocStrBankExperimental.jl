```Julia
密度 : [ML⁻³], [FL⁻⁴T²], [ML⁻³], [ML⁻³], [ML⁻³]
density(U::UnitSystem,S::UnitSystem) = mass(U,S)/volume(U,S)
density(v::Real,U::UnitSystem,S::UnitSystem) = v/density(U,S)
ML⁻³ [ħ⁻³𝘤³mₑ⁴ϕ⁻³g₀⁻³] 統一

特定質量または `mass` あたりの `volume` または `density` (kg⋅m⁻³)、単位換算係数。

```

Julia julia> density(CGS,Metric) # kg⋅cm³⋅g⁻¹⋅m⁻³ 2³5³ = 1000.0 [kg⋅m⁻³]/[g⋅cm⁻³] ガウス -> メトリック

julia> density(CGS,Brtish) # slug⋅cm³⋅g⁻¹⋅ft⁻³ g₀⁻¹ft⁴lb⁻¹2³5³ = 1.940320331979716 [slug⋅ft⁻³]/[g⋅cm⁻³] ガウス -> ブリティッシュ

julia> density(English,Metric) # kg⋅ft³⋅lb⁻¹⋅m⁻³ ft⁻³lb = 16.018463373960138 [kg⋅m⁻³]/[lbm⋅ft⁻³] イングリッシュ -> メトリック ```
