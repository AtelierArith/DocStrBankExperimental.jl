```Julia
resistivity(U::UnitSystem,S::UnitSystem) = resistance(U,S)*length(U,S)
resistivity(v::Real,U::UnitSystem,S::UnitSystem) = v/resistivity(U,S)
```

Electrical `resistivity` or `resistance` by `length` (Ω⋅m), unit conversion factor.

```Julia
julia> resistance(EMU,Metric) # Ω⋅m⋅abΩ⁻¹⋅cm⁻¹
1.0e-9

julia> resistance(ESU,Metric) # Ω⋅m⋅statΩ⁻¹⋅cm⁻¹
8.987551787368179e11

julia> resistance(Metric,SI2019) # Ω⋅Ω⁻¹
1.0000000005452097
```
