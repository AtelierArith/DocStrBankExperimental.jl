```Julia
volumeheatcapacity : [FL⁻²Θ⁻¹], [FL⁻²Θ⁻¹], [ML⁻¹T⁻²Θ⁻¹], [ML⁻¹T⁻²Θ⁻¹], [ML⁻¹T⁻²Θ⁻¹]
volumeheatcapacity(U::UnitSystem,S::UnitSystem) = entropy(U,S)/volume(U,S)
volumeheatcapacity(v::Real,U::UnitSystem,S::UnitSystem) = v/volumeheatcapacity(U,S)
FL⁻²Θ⁻¹ [kB⋅ħ⁻³𝘤³mₑ³ϕ⁻³g₀⁻³] Unified
```

The `entropy` per `volume` or `volumeheatcapacity` (J⋅K⁻¹⋅m⁻³), unit conversion factor.

```Julia
julia> volumeheatcapacity(Metric,SI2019) # K⋅K⁻¹
NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅2⁻⁴5⁻³ = 1.00000000034(31) [K⁻¹]/[K⁻¹] Metric -> SI2019

julia> volumeheatcapacity(CGS,Metric) # J⋅cm³⋅erg⁻¹⋅m⁻³
2⁻¹5⁻¹ = 0.1 [Pa]/[Ba] Gauss -> Metric

julia> volumeheatcapacity(English,SI2019) # J⋅ft²⋅°R⋅K⁻¹⋅lb⁻¹⋅m⁻³
NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅g₀⋅ft⁻²lb⋅2⁻⁴3²5⁻⁴ = 86.184466194(27) [kg⋅m⁻¹s⁻²K⁻¹]/[lbf⋅ft⁻²°R⁻¹] English -> SI2019

julia> volumeheatcapacity(Survey,English) # ftUS⁵°R⋅°ft⁻⁵⋅°R⁻¹
ft²ftUS⁻² = 0.9999960000040004 [ft⁻²]/[ft⁻²] Survey -> English
```
