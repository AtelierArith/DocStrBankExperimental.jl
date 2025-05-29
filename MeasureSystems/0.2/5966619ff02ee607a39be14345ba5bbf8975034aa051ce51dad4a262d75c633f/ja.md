```Julia
molarmass(U::UnitSystem) = avogadro(U)*electronmass(U)/electronunit(U)
molarmass : [MN⁻¹], [FL⁻¹T²N⁻¹], [MN⁻¹], [MN⁻¹], [MN⁻¹]
MN⁻¹ [Mᵤ] 統一

モル質量定数 `Mᵤ` は、化学物質の `molarmass` と `relativemass` の比率です。

```

Julia julia> molarmass(CGS) # g⋅mol⁻¹ 𝟏 = 1.0 [g⋅mol⁻¹] ガウス

julia> molarmass(Metric) # kg⋅mol⁻¹ 2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] メトリック

julia> molarmass(SI2019) # kg⋅mol⁻¹ NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2 = 0.00099999999966(31) [kg⋅mol⁻¹] SI2019

julia> molarmass(International) # kg⋅mol⁻¹ Ωᵢₜ⋅Vᵢₜ⁻²2⁻³5⁻³ = 0.0009998350000179567 [kg⋅mol⁻¹] インターナショナル ```
