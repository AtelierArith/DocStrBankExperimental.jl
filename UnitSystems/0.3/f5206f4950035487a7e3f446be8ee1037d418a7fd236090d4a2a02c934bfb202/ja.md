```Julia
thermalconductance(U::UnitSystem,S::UnitSystem) = thermalconductivity(U,S)*length(U,S)
thermalconductance(v::Real,U::UnitSystem,S::UnitSystem) = v/thermalconductance(U,S)
```

`thermalresistance` の逆数 (W⋅K⁻¹)、単位変換係数。

```Julia
julia> thermalconductance(Metric,SI2019) # K⋅K⁻¹
1.000000000343744

julia> thermalconductance(CGS,Metric) # W⋅s⋅erg⁻¹
1.0000000000000002e-7

julia> thermalconductance(English,Metric) # J⋅°R⋅K⁻¹⋅ft⁻¹⋅lb⁻¹
2.4404723069965204
```
