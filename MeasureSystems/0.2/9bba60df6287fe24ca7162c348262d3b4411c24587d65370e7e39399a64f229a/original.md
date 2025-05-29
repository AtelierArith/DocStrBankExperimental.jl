```Julia
molarenergy : [FLN⁻¹], [FLN⁻¹], [ML²T⁻²N⁻¹], [ML²T⁻²N⁻¹], [ML²T⁻²N⁻¹]
molarenergy(U::UnitSystem,S::UnitSystem) = energy(U,S)/molaramount(U,S)
molarenergy(v::Real,U::UnitSystem,S::UnitSystem) = v/molarenergy(U,S)
FLN⁻¹ [𝘤²Mᵤ⋅g₀⁻¹] Unified
```

Gibbs free `energy` per `mole` or `molarenergy` (J⋅mol⁻¹), unit conversion factor.

```Julia
julia> molarenergy(CGS,Metric) # J⋅erg⁻¹
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] Gauss -> Metric

julia> molarenergy(English,SI2019) # J⋅slug-mol⋅ft⁻¹⋅lb⁻¹⋅mol⁻¹
NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⋅ft⋅2 = 0.00298906691897(92) [J⋅mol⁻¹]/[lbf⋅ft⋅lb-mol⁻¹] English -> SI2019
```
