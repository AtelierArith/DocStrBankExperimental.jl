```Julia
magneticdipolemoment : [L²T⁻¹QA⁻¹C⁻¹], [L²T⁻¹Q], [L²T⁻¹Q], [M¹ᐟ²L⁵ᐟ²T⁻¹], [M¹ᐟ²L⁷ᐟ²T⁻²]
magneticdipolemoment(U::UnitSystem,S::UnitSystem) = current(U,S)*lorentz(U,S)/area(U,S)/gravity(U,S)/angle(U,S)
magneticdipolemoment(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticdipolemoment(U,S)
L²T⁻¹QA⁻¹C⁻¹ [ħ³ᐟ²𝘤⁻¹ᐟ²μ₀⁻¹ᐟ²mₑ⁻¹ϕ¹ᐟ²λ⁻¹ᐟ²g₀] Unified
```

Magnetic dipole moment or `magneticdipolemoment` (J⋅T⁻¹, A⋅m²), unit conversion factor.

```Julia
julia> magneticdipolemoment(EMU,Metric) # J⋅G⋅T⁻¹⋅erg⁻¹
2⁻³5⁻³ = 0.001 [m²C]/[g¹ᐟ²cm⁵ᐟ²] EMU -> Metric

julia> magneticdipolemoment(ESU,Metric) # J⋅statT⋅T⁻¹⋅erg⁼¹
𝘤⁻¹2⁻⁵5⁻⁵ = 3.335640951981521×10⁻¹⁴ [m²C]/[g¹ᐟ²cm⁷ᐟ²s⁻¹] ESU -> Metric

julia> magneticdipolemoment(Metric,SI2019) # A⋅A⁻¹⋅
𝘩⁻¹ᐟ²𝘤¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019
```
