```Julia
specificentropy : [FM⁻¹LΘ⁻¹], [L²T⁻²Θ⁻¹], [L²T⁻²Θ⁻¹], [L²T⁻²Θ⁻¹], [L²T⁻²Θ⁻¹]
specificentropy(U::UnitSystem,S::UnitSystem) = specificenergy(U,S)/temperature(U,S)
specificentropy(v::Real,U::UnitSystem,S::UnitSystem) = v/specificentropy(U,S)
FM⁻¹LΘ⁻¹ [kB⋅mₑ⁻¹] 統一

比熱容量または `specificentropy` (J⋅K⁻¹⋅kg⁻¹)、単位換算係数。

```

Julia julia> specificentropy(Metric,SI2019) # m²⋅K⋅K⁻¹⋅cm⁻² NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅2⁻⁴5⁻³ = 1.00000000034(31) [K⁻¹]/[K⁻¹] Metric -> SI2019

julia> specificentropy(CGS,Metric) # m²⋅cm⁻² 2⁻⁴5⁻⁴ = 0.0001 [J⋅kg⁻¹]/[erg⋅g⁻¹] Gauss -> Metric

julia> specificentropy(English,Metric) # m²⋅°R⋅K⁻¹⋅ft⁻² g₀⋅ft⋅3²5⁻¹ = 5.380320456 [J⋅K⁻¹kg⁻¹]/[lbf⋅lbm⁻¹ft⋅°R⁻¹] English -> Metric

julia> specificentropy(Survey,English) # ft²⋅°R⋅ftUS⁻²⋅°R⁻¹ ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] Survey -> English ```
