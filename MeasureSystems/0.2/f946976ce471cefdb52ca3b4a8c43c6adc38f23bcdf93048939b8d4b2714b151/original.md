```Julia
darcy(U::UnitSystem) = area(milli/atm,U,Gauss)
area : [L²], [L²], [L²], [L²], [L²]
L²⋅(R∞²α⁻⁴atm⁻¹τ²2⁻⁵5⁻⁷ = 6.6183611583(41) × 10¹²) [ħ²𝘤⁻²mₑ⁻²ϕ²g₀²] Unified
```

Metric unit of permeability (m² or ft²).

```Julia
julia> darcy(Metric) # m²
atm⁻¹2⁻⁷5⁻⁷ = 9.869232667160128×10⁻¹³ [m²] Metric

julia> darcy(CGS) # cm²
atm⁻¹2⁻³5⁻³ = 9.86923266716013×10⁻⁹ [cm²] Gauss

julia> darcy(English) # ft²
ft⁻²atm⁻¹2⁻⁷5⁻⁷ = 1.0623153631097675×10⁻¹¹ [ft²] English
```
