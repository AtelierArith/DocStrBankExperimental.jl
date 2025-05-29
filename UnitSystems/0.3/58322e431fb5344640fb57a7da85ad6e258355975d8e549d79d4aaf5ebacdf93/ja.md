```Julia
thermalresistance(U::UnitSystem,S::UnitSystem) = 1/thermalconductivity(U,S)/length(U,S)
thermalresistance(v::Real,U::UnitSystem,S::UnitSystem) = v/thermalresistance(U,S)
```

熱流に対する抵抗または `thermalresistance` (K⋅W⁻¹)、単位変換係数。

```Julia
julia> thermalresistance(Metric,SI2019) # K⋅K⁻¹
0.9999999996562561

julia> thermalresistance(CGS,Metric) # erg⋅s⁻¹⋅W⁻¹
9.999999999999998e6

julia> thermalresistance(English,Metric) # ft⋅lb⋅K⋅°R⁻¹⋅J⁻¹
0.40975674959848074
```
