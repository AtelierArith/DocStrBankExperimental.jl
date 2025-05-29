```Julia
resistance(U::UnitSystem,S::UnitSystem) = electricpotential(U,S)/current(U,S)
resistance(v::Real,U::UnitSystem,S::UnitSystem) = v/resistance(U,S)
```

Electrical `resistance` or `electricpotential` per `current` (Ω, S⁻¹, V⋅A⁻¹), unit conversion factor.

```Julia
julia> resistance(EMU,Metric) # Ω⋅abΩ⁻¹
1.0e-9

julia> resistance(ESU,Metric) # Ω⋅statΩ⁻¹
8.987551787368179e11

julia> resistance(Metric,SI2019) # Ω⋅Ω⁻¹
1.0000000005452097
```
