```Julia
angularwavenumber : [L⁻¹A], [L⁻¹], [L⁻¹], [L⁻¹], [L⁻¹]
angularwavenumber(U::UnitSystem,S::UnitSystem) = angle(U,S)/length(U,S)
angularwavenumber(v::Real,U::UnitSystem,S::UnitSystem) = v/angularwavenumber(U,S)
L⁻¹A [ħ⁻¹𝘤⋅mₑ⋅g₀⁻¹] Unified
```

Number of occurences per unit of space (m⁻¹), unit conversion factor.

```Julia
julia> angularwavenumber(CGS,Metric) # cm⋅m⁻¹
2²5² = 100.0 [m⁻¹]/[cm⁻¹] Gauss -> Metric

julia> angularwavenumber(English,Metric) # ft⋅m⁻¹
ft⁻¹ = 3.280839895013123 [m⁻¹]/[ft⁻¹] English -> Metric
```
