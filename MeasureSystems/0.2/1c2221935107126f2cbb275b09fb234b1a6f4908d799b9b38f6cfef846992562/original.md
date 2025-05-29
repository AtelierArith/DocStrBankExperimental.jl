```Julia
electricdipolemoment : [LQ], [LQ], [LQ], [M¹ᐟ²L³ᐟ²], [M¹ᐟ²L⁵ᐟ²T⁻¹]
electricdipolemoment(U::UnitSystem,S::UnitSystem) = charge(U,S)*length(U,S)
electricdipolemoment(v::Real,U::UnitSystem,S::UnitSystem) = v/electricdipolemoment(U,S)
LQ [ħ³ᐟ²𝘤⁻³ᐟ²μ₀⁻¹ᐟ²mₑ⁻¹ϕ³ᐟ²λ⁻¹ᐟ²αL⁻¹g₀] Unified
```

Electric dipole moment or `electricdipolemoment` (C⋅m), unit conversion factor.

```Julia
julia> electricdipolemoment(EMU,Metric) # C⋅m⋅abC⁻¹⋅cm⁻¹
2⁻¹5⁻¹ = 0.1 [m⋅C]/[g¹ᐟ²cm³ᐟ²] EMU -> Metric

julia> electricdipolemoment(ESU,Metric) # C⋅m⋅statC⁻¹⋅cm⁼¹
𝘤⁻¹2⁻³5⁻³ = 3.3356409519815203×10⁻¹² [m⋅C]/[g¹ᐟ²cm⁵ᐟ²s⁻¹] ESU -> Metric

julia> electricdipolemoment(Metric,SI2019) # C⋅C⁻¹
𝘩⁻¹ᐟ²𝘤¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019
```
