```Julia
fuelefficiency : [L⁻²], [L⁻²], [L⁻²], [L⁻²], [L⁻²]
fuelefficiency(U::UnitSystem,S::UnitSystem) = 1/area(U,S)
fuelefficiency(v::Real,U::UnitSystem,S::UnitSystem) = v/fuelefficiency(U,S)
L⁻² [ħ⁻²𝘤²mₑ²ϕ⁻²g₀⁻²] Unified
```

Distance per volume or fuel efficiency (m⋅m⁻³, m⁻²), unit conversion factor.

```Julia
julia> fuelefficiency(CGS,Metric) # cm²⋅m⁻²
2⁴5⁴ = 10000.0 [m⁻²]/[cm⁻²] Gauss -> Metric

julia> fuelefficiency(English,Metric) # ft²⋅m⁻²
ft⁻² = 10.76391041670972 [m⁻²]/[ft⁻²] English -> Metric
```
