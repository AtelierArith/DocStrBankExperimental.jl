```Julia
thermalconductance(U::UnitSystem,S::UnitSystem) = thermalconductivity(U,S)*length(U,S)
thermalconductance(v::Real,U::UnitSystem,S::UnitSystem) = v/thermalconductance(U,S)
```

Reciprocal of `thermalresistance` (W⋅K⁻¹), unit conversion factor.

```Julia
julia> thermalconductance(Metric,SI2019) # K⋅K⁻¹
1.000000000343744

julia> thermalconductance(CGS,Metric) # W⋅s⋅erg⁻¹
1.0000000000000002e-7

julia> thermalconductance(English,Metric) # J⋅°R⋅K⁻¹⋅ft⁻¹⋅lb⁻¹
2.4404723069965204
```
