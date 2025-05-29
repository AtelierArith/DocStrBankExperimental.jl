```Julia
electricfield : [FQ⁻¹], [FQ⁻¹], [MLT⁻²Q⁻¹], [M¹ᐟ²L¹ᐟ²T⁻²], [M¹ᐟ²L⁻¹ᐟ²T⁻¹]
electricfield(U::UnitSystem,S::UnitSystem) = electricpotential(U,S)/length(U,S)
electricfield(v::Real,U::UnitSystem,S::UnitSystem) = v/electricfield(U,S)
FQ⁻¹ [ħ⁻³ᐟ²𝘤⁷ᐟ²μ₀¹ᐟ²mₑ²ϕ⁻³ᐟ²λ¹ᐟ²αL⋅g₀⁻²] Unified
```

The `electricpotential` per `length` or `electricfield` (V⋅m⁻¹), unit conversion factor.

```Julia
julia> electricfield(EMU,Metric) # V⋅cm⋅abV⁻¹⋅m⁻¹
2⁻⁶5⁻⁶ = 1.0×10⁻⁶ [V⋅m⁻¹]/[g¹ᐟ²cm¹ᐟ²s⁻²] EMU -> Metric

julia> electricfield(EMU,ESU) # statV⋅abV⁻¹
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [g⁻¹ᐟ²cm⁻³ᐟ²s]/[g⁻¹ᐟ²cm⁻¹ᐟ²] EMU -> ESU

julia> electricfield(ESU,Metric) # V⋅cm⋅statV⁻¹⋅m⁻¹
𝘤⋅2⁻⁴5⁻⁴ = 29979.2458 [V⋅m⁻¹]/[g¹ᐟ²cm⁻¹ᐟ²s⁻¹] ESU -> Metric

julia> electricfield(Metric,SI2019) # V⋅V⁻¹
𝘩¹ᐟ²𝘤⁻¹ᐟ²𝘦⁻¹α¹ᐟ²τ⁻¹ᐟ²2⁷ᐟ²5⁷ᐟ² = 1.000000000273(77) [C⁻¹]/[C⁻¹] Metric -> SI2019
```
