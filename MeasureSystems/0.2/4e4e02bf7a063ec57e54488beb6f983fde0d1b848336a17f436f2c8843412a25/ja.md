```Julia
molarmass : [MN⁻¹], [FL⁻¹T²N⁻¹], [MN⁻¹], [MN⁻¹], [MN⁻¹]
molarmass(U::UnitSystem,S::UnitSystem) = molarmass(S)/molarmass(U)
molarmass(v::Real,U::UnitSystem,S::UnitSystem) = v/molarmass(U,S)
MN⁻¹ [Mᵤ] 統一

モル質量または `質量` あたり `モル` (kg⋅mol⁻¹)、単位換算係数。

```

Julia julia> molarmass(CGS,Metric) # kg⋅g⁻¹ 2⁻³5⁻³ = 0.001 [kg]/[g] ガウス -> メトリック

julia> molarmass(Metric,SI2019) # mol⋅mol⁻¹ NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 0.99999999966(31) [mol⁻¹]/[mol⁻¹] メトリック -> SI2019 ```
