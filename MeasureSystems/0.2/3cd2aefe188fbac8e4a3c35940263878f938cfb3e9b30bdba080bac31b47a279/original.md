```Julia
magneticfield : [L⁻¹T⁻¹QRC⁻¹], [L⁻¹T⁻¹Q], [L⁻¹T⁻¹Q], [M¹ᐟ²L⁻¹ᐟ²T⁻¹], [M¹ᐟ²L¹ᐟ²T⁻²]
magneticfield(U::UnitSystem,S::UnitSystem) = current(U,S)*rationalization(U,S)*lorentz(U,S)/length(U,S)
magneticfield(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticfield(U,S)
L⁻¹T⁻¹QRC⁻¹ [ħ⁻³ᐟ²𝘤⁵ᐟ²μ₀⁻¹ᐟ²mₑ²ϕ⁻³ᐟ²λ¹ᐟ²g₀⁻²] Unified
```

Magnetization or `magneticfield` or `current` per `length` (A⋅m⁻¹), unit conversion factor.

```Julia
julia> magneticfield(EMU,Metric) # A⋅m⁻¹⋅Oe⁻¹
τ⁻¹2²5³ = 79.57747154594767 [m⁻¹C]/[g¹ᐟ²cm⁻¹ᐟ²] EMU -> Metric

julia> magneticfield(ESU,Metric) # A⋅cm⋅m⁻¹⋅statA⁻¹
𝘤⁻¹τ⁻¹5 = 2.6544187294380726×10⁻⁹ [m⁻¹C]/[g¹ᐟ²cm¹ᐟ²s⁻¹] ESU -> Metric

julia> magneticfield(Metric,SI2019) # A⋅A⁻¹
𝘩⁻¹ᐟ²𝘤¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019
```
