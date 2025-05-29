```Julia
irradiance(U::UnitSystem,S::UnitSystem) = power(U,S)/area(U,S)
irradiance(v::Real,U::UnitSystem,S::UnitSystem) = v/irradiance(U,S)
```

Heat flux density or irradiance or `power` per `area` (W⋅m⁻², kg⋅s⁻³), unit conversion factor.

```Julia
julia> irradiance(CGS,Metric) # kg⋅g⁻¹
0.0009999999999999996

julia> irradiance(CGS,English) # lb⋅g⁻¹
6.852176585679174e-5

julia> irradiance(English,Metric) # kg⋅lb⁻¹
14.593902937206364
```
