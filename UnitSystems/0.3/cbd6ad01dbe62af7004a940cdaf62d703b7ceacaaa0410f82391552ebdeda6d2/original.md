```Julia
thermalexpansion(U::UnitSystem,S::UnitSystem) = 1/temperature(U,S)
thermalexpansion(v::Real,U::UnitSystem,S::UnitSystem) = v/thermalexpansion(U,S)
```

Measurement scale for coefficient of `thermalexpansion` (K⁻¹), unit conversion factor.

```Julia
julia> thermalexpansion(Metric,SI2019) # K⋅K⁻¹
1.000000000343744

julia> thermalexpansion(English,SI2019) # °R⋅K⁻¹
1.8000000006187389

julia> thermalexpansion(English,Metric) # °R⋅K⁻¹
1.7999999999999998
```
