```Julia
magneticmoment : [FL²TQ⁻¹C], [FL²TQ⁻¹], [ML³T⁻¹Q⁻¹], [M¹ᐟ²L⁵ᐟ²T⁻¹], [M¹ᐟ²L³ᐟ²]
magneticmoment(U::UnitSystem,S::UnitSystem) = magneticflux(U,S)*length(U,S)
magneticmoment(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticmoment(U,S)
FL²TQ⁻¹C [ħ³ᐟ²𝘤⁻¹ᐟ²μ₀¹ᐟ²mₑ⁻¹ϕ³ᐟ²λ¹ᐟ²g₀] Unified
```

Amount of `magneticmoment` or `magneticflux` by `length` (Wb⋅m or T⋅m³), unit conversion factor.

```Julia
julia> magneticmoment(EMU,Metric) # Wb⋅m⋅Mx⁻¹⋅cm⁻¹
2⁻¹⁰5⁻¹⁰ = 1.0×10⁻¹⁰ [V⋅m]/[g¹ᐟ²cm⁵ᐟ²s⁻²] EMU -> Metric

julia> magneticmoment(ESU,Metric) # Wb⋅m⋅statWb⁻¹⋅cm⁻¹
𝘤⋅2⁻⁸5⁻⁸ = 2.9979245800000003 [V⋅m]/[g¹ᐟ²cm³ᐟ²s⁻¹] ESU -> Metric

julia> magneticmoment(Metric,SI2019) # Wb⋅Wb⁻¹
𝘩¹ᐟ²𝘤⁻¹ᐟ²𝘦⁻¹α¹ᐟ²τ⁻¹ᐟ²2⁷ᐟ²5⁷ᐟ² = 1.000000000273(77) [C⁻¹]/[C⁻¹] Metric -> SI2019
```
