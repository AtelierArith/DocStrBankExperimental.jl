```Julia
electricflux : [FL²Q⁻¹], [FL²Q⁻¹], [ML³T⁻²Q⁻¹], [M¹ᐟ²L⁵ᐟ²T⁻²], [M¹ᐟ²L³ᐟ²T⁻¹]
electricflux(U::UnitSystem,S::UnitSystem) = electricpotential(U,S)*length(U,S)
electricflux(v::Real,U::UnitSystem,S::UnitSystem) = v/electricflux(U,S)
FL²Q⁻¹ [ħ¹ᐟ²𝘤³ᐟ²μ₀¹ᐟ²ϕ¹ᐟ²λ¹ᐟ²αL] Unified
```

Amount of `electricflux` or `electricpotential` by `length` (V⋅m), unit conversion factor.

```Julia
julia> electricflux(EMU,Metric) # V⋅m⋅abV⁻¹⋅cm⁻¹
2⁻¹⁰5⁻¹⁰ = 1.0×10⁻¹⁰ [V⋅m]/[g¹ᐟ²cm⁵ᐟ²s⁻²] EMU -> Metric

julia> electricflux(EMU,ESU) # statV⋅abV⁻¹
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [g⁻¹ᐟ²cm⁻³ᐟ²s]/[g⁻¹ᐟ²cm⁻¹ᐟ²] EMU -> ESU

julia> electricflux(ESU,Metric) # V⋅m⋅statV⁻¹⋅cm⁻¹
𝘤⋅2⁻⁸5⁻⁸ = 2.9979245800000003 [V⋅m]/[g¹ᐟ²cm³ᐟ²s⁻¹] ESU -> Metric

julia> electricflux(Metric,SI2019) # V⋅V⁻¹
𝘩¹ᐟ²𝘤⁻¹ᐟ²𝘦⁻¹α¹ᐟ²τ⁻¹ᐟ²2⁷ᐟ²5⁷ᐟ² = 1.000000000273(77) [C⁻¹]/[C⁻¹] Metric -> SI2019
```
