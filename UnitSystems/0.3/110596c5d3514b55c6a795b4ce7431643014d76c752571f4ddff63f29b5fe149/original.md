```Julia
thermalresistivity(U::UnitSystem,S::UnitSystem) = 1/thermalconductivity(U,S)
thermalresistivity(v::Real,U::UnitSystem,S::UnitSystem) = v/thermalresistivity(U,S)
```

Resistance to heat flow or `thermalresistance` (K⋅W⁻¹), unit conversion factor.

```Julia
julia> thermalresistance(Metric,SI2019) # K⋅K⁻¹
0.9999999996562561

julia> thermalresistance(CGS,Metric) # erg⋅s⁻¹⋅W⁻¹
9.999999999999998e6

julia> thermalresistance(English,Metric) # ft⋅lb⋅K⋅°R⁻¹⋅J⁻¹
0.40975674959848074
```
