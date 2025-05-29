```Julia
charge : [Q], [Q], [Q], [M¹ᐟ²L¹ᐟ²], [M¹ᐟ²L³ᐟ²T⁻¹]
charge(U::UnitSystem,S::UnitSystem) = sqrt(action(U,S)*current(U,S)/electricpotential(U,S))
charge(v::Real,U::UnitSystem,S::UnitSystem) = v/charge(U,S)
Q [ħ¹ᐟ²𝘤⁻¹ᐟ²μ₀⁻¹ᐟ²ϕ¹ᐟ²λ⁻¹ᐟ²αL⁻¹] 統一

電気 `charge` の量子化 (C, A⋅s)、単位変換係数。

```

Julia julia> charge(EMU,Metric) # C⋅abC⁻¹ 2⋅5 = 10.0 [C]/[g¹ᐟ²cm¹ᐟ²] EMU -> Metric

julia> charge(EMU,ESU) # stC⋅abC⁻¹ 𝘤⋅2²5² = 2.99792458×10¹⁰ [g¹ᐟ²cm³ᐟ²s⁻¹]/[g¹ᐟ²cm¹ᐟ²] EMU -> ESU

julia> charge(ESU,Metric) # C⋅stC⁻¹ 𝘤⁻¹2⁻¹5⁻¹ = 3.3356409519815207×10⁻¹⁰ [C]/[g¹ᐟ²cm³ᐟ²s⁻¹] ESU -> Metric

julia> charge(Metric,SI2019) # C⋅C⁻¹ 𝘩⁻¹ᐟ²𝘃¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019

julia> charge(Hartree,SI2019) # C⋅𝘦⁻¹ 𝘦 = 1.602176634×10⁻¹⁹ [C]/[𝘦] Hartree -> SI2019 ```
