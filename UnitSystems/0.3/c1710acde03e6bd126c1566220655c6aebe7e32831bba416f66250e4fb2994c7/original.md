```Julia
massflow(U::UnitSystem,S::UnitSystem) = mass(U,S)/time(U,S)
massflow(v::Real,U::UnitSystem,S::UnitSystem) = v/massflow(U,S)
```

Rate of `massflow` or `mass` per `time` (kg⋅s⁻¹), unit conversion factor.

```Julia
julia> massflow(CGS,Metric) # kg⋅g⁻¹
0.001

julia> massflow(CODATA,Metric) # kg⋅kg⁻¹
1.000000016738611

julia> massflow(Conventional,Metric) # kg⋅kg⁻¹
1.000000195536555

julia> massflow(English,Metric) # kg⋅slug⁻¹
0.45359237
```
