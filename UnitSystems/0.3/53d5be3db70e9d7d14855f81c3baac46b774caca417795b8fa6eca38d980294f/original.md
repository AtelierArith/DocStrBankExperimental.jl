```Julia
thermalconductivity(U::UnitSystem,S::UnitSystem) = force(U,S)/time(U,S)/temperature(U,S)
thermalconductivity(v::Real,U::UnitSystem,S::UnitSystem) = v/thermalconductivity(U,S)
```

Heat conductivity or `thermalconductivity` (W⋅m⁻¹⋅K⁻¹), unit conversion factor.

```Julia
julia> thermalconductivity(Metric,SI2019) # K⋅K⁻¹
1.000000000343744

julia> thermalconductivity(CGS,Metric) # N⋅dyn⁻¹
1.0e-5

julia> thermalconductivity(English,Metric) # N⋅°R⋅K⁻¹⋅ft⁻¹⋅lb⁻¹
8.006798907468898
```
