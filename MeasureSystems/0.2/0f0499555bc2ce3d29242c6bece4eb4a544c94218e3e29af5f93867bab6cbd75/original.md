```Julia
angularlength : [LA⁻¹], [L], [L], [L], [L]
angularlength(U::UnitSystem,S::UnitSystem) = length(U,S)/angle(U,S)
angularlength(v::Real,U::UnitSystem,S::UnitSystem) = v/angularlength(U,S)
LA⁻¹ [ħ⋅𝘤⁻¹mₑ⁻¹g₀] Unified
```

Unit of `length` per `angle` (m⋅rad⁻¹), unit conversion factor.

```Julia
julia> angularlength(CGS,Metric) # cm⋅m⁻¹
2⁻²5⁻² = 0.010000000000000002 [m]/[cm] Gauss -> Metric

julia> angularlength(English,Metric) # ft⋅m⁻¹
ft = 0.3048 [m]/[ft] English -> Metric
```
