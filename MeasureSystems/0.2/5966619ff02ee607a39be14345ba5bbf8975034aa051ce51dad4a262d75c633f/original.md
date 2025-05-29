```Julia
molarmass(U::UnitSystem) = avogadro(U)*electronmass(U)/electronunit(U)
molarmass : [MN⁻¹], [FL⁻¹T²N⁻¹], [MN⁻¹], [MN⁻¹], [MN⁻¹]
MN⁻¹ [Mᵤ] Unified
```

Molar mass constant `Mᵤ` is the ratio of the `molarmass` and `relativemass` of a chemical.

```Julia
julia> molarmass(CGS) # g⋅mol⁻¹
𝟏 = 1.0 [g⋅mol⁻¹] Gauss

julia> molarmass(Metric) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] Metric

julia> molarmass(SI2019) # kg⋅mol⁻¹
NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2 = 0.00099999999966(31) [kg⋅mol⁻¹] SI2019

julia> molarmass(International) # kg⋅mol⁻¹
Ωᵢₜ⋅Vᵢₜ⁻²2⁻³5⁻³ = 0.0009998350000179567 [kg⋅mol⁻¹] International
```
