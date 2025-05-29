```Julia
currentdensity(U::UnitSystem,S::UnitSystem) = current(U,S)/area(U,S)
currentdensity(v::Real,U::UnitSystem,S::UnitSystem) = v/currentdensity(U,S)
```

Cross-section `currentdensity` or `current` per `area` (A⋅m⁻²), unit conversion factor.

```Julia
julia> currentdensity(EMU,Metric) # A⋅cm²⋅Bi⁻¹⋅m⁻²
99999.99999999996

julia> currentdensity(ESU,Metric) # A⋅cm²⋅statA⁻¹⋅m⁼²
3.335640951981519e-6

julia> currentdensity(Metric,SI2019) # A⋅A⁻¹
0.9999999997273952
```
