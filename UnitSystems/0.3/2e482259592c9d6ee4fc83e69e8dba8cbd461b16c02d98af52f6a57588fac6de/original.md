```Julia
spectralflux(U::UnitSystem,S::UnitSystem) = power(U,S)/length(U,S)
spectralflux(v::Real,U::UnitSystem,S::UnitSystem) = v/spectralflux(U,S)
```

Spectral power or `power` per wave `length` (W⋅m⁻¹), unit conversion factor.

```Julia
julia> spectralflux(CGS,Metric) # kg⋅m⋅g⁻¹⋅cm⁻¹
9.999999999999999e-6

julia> spectralflux(CGS,English) # lb⋅ft⋅g⁻¹⋅cm⁻¹
2.2480894309971044e-6

julia> spectralflux(English,Metric) # kg⋅m⋅lb⁻¹⋅ft⁻¹
4.4482216152605
```
