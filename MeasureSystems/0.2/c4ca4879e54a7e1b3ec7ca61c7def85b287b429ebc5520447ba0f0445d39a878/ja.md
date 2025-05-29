```Julia
exposure : [M⁻¹Q], [F⁻¹LT⁻²Q], [M⁻¹Q], [M⁻¹ᐟ²L¹ᐟ²], [M⁻¹ᐟ²L³ᐟ²T⁻¹]
exposure(U::UnitSystem,S::UnitSystem) = charge(U,S)/mass(U,S)
exposure(v::Real,U::UnitSystem,S::UnitSystem) = v/exposure(U,S)
M⁻¹Q [ħ¹ᐟ²𝘤⁻¹ᐟ²μ₀⁻¹ᐟ²mₑ⁻¹ϕ¹ᐟ²λ⁻¹ᐟ²αL⁻¹] 統一

イオン化放射線 `exposure` または `mass` あたりの `charge` (C⋅kg⁻¹)、単位換算係数。

```

Julia julia> exposure(EMU,Metric) # C⋅g⋅abC⁻¹⋅kg 2⁴5⁴ = 10000.0 [kg⁻¹C]/[g⁻¹ᐟ²cm¹ᐟ²] EMU -> Metric

julia> exposure(EMU,ESU) # statC⋅abC⁻¹ 𝘤⋅2²5² = 2.99792458×10¹⁰ [g¹ᐟ²cm³ᐟ²s⁻¹]/[g¹ᐟ²cm¹ᐟ²] EMU -> ESU

julia> expsure(ESU,Metric) # C⋅g⋅statC⁻¹⋅kg 𝘤⁻¹2²5² = 3.3356409519815204×10⁻⁷ [kg⁻¹C]/[g⁻¹ᐟ²cm³ᐟ²s⁻¹] ESU -> Metric

julia> exposure(Metric,SI2019) # C⋅C⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019 ```
