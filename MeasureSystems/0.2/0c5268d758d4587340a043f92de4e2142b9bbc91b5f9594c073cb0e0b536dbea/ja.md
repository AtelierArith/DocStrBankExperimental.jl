```Julia
electricpotential : [FLQ⁻¹], [FLQ⁻¹], [ML²T⁻²Q⁻¹], [M¹ᐟ²L³ᐟ²T⁻²], [M¹ᐟ²L¹ᐟ²T⁻¹]
electricpotential(U::UnitSystem,S::UnitSystem) = energy(U,S)/charge(U,S)
electricpotential(v::Real,U::UnitSystem,S::UnitSystem) = v/electricpotential(U,S)
FLQ⁻¹ [ħ⁻¹ᐟ²𝘃⁵ᐟ²μ₀¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ¹ᐟ²αL⋅g₀⁻¹] 統一

電圧または `electricpotential` または `energy` あたりの `charge` (V, J⋅C⁻¹)、単位換算係数。

```

Julia julia> electricpotential(EMU,Metric) # V⋅abV⁻¹ 2⁻⁸5⁻⁸ = 1.0×10⁻⁸ [V]/[g¹ᐟ²cm³ᐟ²s⁻²] EMU -> Metric

julia> electricpotential(EMU,ESU) # statV⋅abV⁻¹ 𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [g⁻¹ᐟ²cm⁻³ᐟ²s]/[g⁻¹ᐟ²cm⁻¹ᐟ²] EMU -> ESU

julia> electricpotential(ESU,Metric) # V⋅statV⁻¹ 𝘤⋅2⁻⁶5⁻⁶ = 299.792458 [V]/[g¹ᐟ²cm¹ᐟ²s⁻¹] ESU -> Metric

julia> electricpotential(Metric,SI2019) # V⋅V⁻¹ 𝘩¹ᐟ²𝘃⁻¹ᐟ²𝘦⁻¹α¹ᐟ²τ⁻¹ᐟ²2⁷ᐟ²5⁷ᐟ² = 1.000000000273(77) [C⁻¹]/[C⁻¹] Metric -> SI2019 ```
