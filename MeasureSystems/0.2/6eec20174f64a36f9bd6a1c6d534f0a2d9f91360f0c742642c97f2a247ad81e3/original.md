```Julia
magneticpolarizability : [L³A⁻¹R⁻¹], [L³], [L³], [L³], [L³]
magneticpolarizability(U::UnitSystem,S::UnitSystem) = magneticdipolemoment(U,S)/magneticfield(U,S)
magneticpolarizability(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticpolarizability(U,S)
L³A⁻¹R⁻¹ [ħ³𝘤⁻³mₑ⁻³ϕ²λ⁻¹g₀³] Unified
```

Polarizability or `magneticdipolemoment` per `magneticfield` (m³), unit conversion factor.

```Julia
julia> electricpolarizability(EMU,Metric) # m³⋅cm⁻³
2⁵5⁵ = 100000.0 [kg⁻¹s²C²]/[cm⋅s²] EMU -> Metric

julia> electricpolarizability(ESU,Metric) # m³⋅cm⁼³
𝘤⁻²2⋅5 = 1.1126500560536184×10⁻¹⁶ [kg⁻¹s²C²]/[mL] ESU -> Metric

julia> electricpolarizability(Metric,Gauss) # cm³⋅m⁻³
𝘤²2⁻¹5⁻¹ = 8.987551787368176×10¹⁵ [mL]/[kg⁻¹s²C²] Metric -> Gauss

julia> electricpolarizability(Metric,SI2019)
𝘩⁻¹𝘤⋅𝘦²α⁻¹τ⋅2⁻⁷5⁻⁷ = 0.99999999945(15) [C²]/[C²] Metric -> SI2019
```
