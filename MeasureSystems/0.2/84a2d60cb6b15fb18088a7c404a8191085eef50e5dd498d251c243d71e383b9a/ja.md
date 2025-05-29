```Julia
linearchargedensity : [L⁻¹Q], [L⁻¹Q], [L⁻¹Q], [M¹ᐟ²L⁻¹ᐟ²], [M¹ᐟ²L¹ᐟ²T⁻¹]
linearchargedensity(U::UnitSystem,S::UnitSystem) = charge(U,S)/length(U,S)
linearchargedensity(v::Real,U::UnitSystem,S::UnitSystem) = v/linearchargedensity(U,S)
L⁻¹Q [ħ⁻¹ᐟ²𝘤¹ᐟ²μ₀⁻¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ⁻¹ᐟ²αL⁻¹g₀⁻¹] 統一

`linearchargedensity` または `charge` の `length` あたりの量 (C⋅m⁻¹)、単位変換係数。

```

Julia julia> linearchargedensity(EMU,Metric) # C⋅cm⋅abC⁻¹⋅m⁻¹ 2³5³ = 1000.0 [m⁻¹C]/[g¹ᐟ²cm⁻¹ᐟ²] EMU -> Metric

julia> linearchargedensity(ESU,Metric) # C⋅cm⋅statC⁻¹⋅m⁼¹ 𝘤⁻¹2⋅5 = 3.3356409519815205×10⁻⁸ [m⁻¹C]/[g¹ᐟ²cm¹ᐟ²s⁻¹] ESU -> Metric

julia> linearchargedensity(Metric,SI2019) # C⋅C⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019 ```
