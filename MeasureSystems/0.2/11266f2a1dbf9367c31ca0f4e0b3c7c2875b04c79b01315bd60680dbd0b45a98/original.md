```Julia
magneticfluxdensity : [FL⁻¹TQ⁻¹C], [FL⁻¹TQ⁻¹], [MT⁻¹Q⁻¹], [M¹ᐟ²L⁻¹ᐟ²T⁻¹], [M¹ᐟ²L⁻³ᐟ²]
magneticfluxdensity(U::UnitSystem,S::UnitSystem) = magneticflux(U,S)/area(U,S)
magneticfluxdensity(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticfluxdensity(U,S)
FL⁻¹TQ⁻¹C [ħ⁻³ᐟ²𝘤⁵ᐟ²μ₀¹ᐟ²mₑ²ϕ⁻³ᐟ²λ¹ᐟ²g₀⁻²] Unified
```

Magnetic induction or `magneticmoment` per `volume` (T or Wb⋅m⁻²), unit conversion factor.

```Julia
julia> magneticfluxdensity(EMU,Metric) # T⋅G⁻¹
2⁻⁴5⁻⁴ = 0.0001 [kg⋅s⁻²C⁻¹]/[g¹ᐟ²cm⁻¹ᐟ²s⁻²] EMU -> Metric

julia> magneticfluxdensity(EMU,ESU) # statT⋅G⁻¹
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [g⁻¹ᐟ²cm⁻³ᐟ²s]/[g⁻¹ᐟ²cm⁻¹ᐟ²] EMU -> ESU

julia> magneticfluxdensity(Metric,SI2019) # T⋅T⁻¹
𝘩¹ᐟ²𝘤⁻¹ᐟ²𝘦⁻¹α¹ᐟ²τ⁻¹ᐟ²2⁷ᐟ²5⁷ᐟ² = 1.000000000273(77) [C⁻¹]/[C⁻¹] Metric -> SI2019
```
