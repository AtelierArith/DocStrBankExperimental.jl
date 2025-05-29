```Julia
lineardensity : [ML⁻¹], [FL⁻²T²], [ML⁻¹], [ML⁻¹], [ML⁻¹]
lineardensity(U::UnitSystem,S::UnitSystem) = mass(U,S)/length(U,S)
lineardensity(v::Real,U::UnitSystem,S::UnitSystem) = v/lineardensity(U,S)
ML⁻¹ [ħ⁻¹𝘤⋅mₑ²ϕ⁻¹g₀⁻¹] 統一

`lineardensity` または `mass` の `length` あたりの量 (kg⋅m⁻¹)、単位変換係数。

```

Julia julia> lineardensity(CGS,Metric) # kg⋅cm¹⋅g⁻¹⋅m⁻¹ 2⁻¹5⁻¹ = 0.1 [kg⋅m⁻¹]/[g⋅cm⁻¹] ガウス -> メトリック

julia> lineardensity(CGS,British) # slug⋅cm¹⋅g⁻¹⋅ft⁻¹ g₀⁻¹ft²lb⁻¹2⁻¹5⁻¹ = 0.002088543423315013 [lb⋅ft⁻²s²]/[g⋅cm⁻¹] ガウス -> ブリティッシュ

julia> lineardensity(English,Metric) # kg⋅ft¹⋅lb⁻¹⋅m⁻¹ ft⁻¹lb = 1.4881639435695537 [kg⋅m⁻¹]/[lbm⋅ft⁻¹] イングリッシュ -> メトリック ```
