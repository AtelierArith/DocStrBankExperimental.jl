```Julia
fluence(U::UnitSystem,S::UnitSystem) = energy(U,S)/area(U,S
fluence(v::Real,U::UnitSystem,S::UnitSystem) = v/fluence(U,S)
```

Radiant exposure or `force` per `length` or stiffness (N⋅m⁻¹, J⋅m⁻²), unit conversion factor.

```Julia
julia> fluence(CGS,Metric) # kg⋅g⁻¹
0.001

julia> fluence(CGS,English) # lb⋅g⁻¹
6.852176585679174e-5

julia> fluence(CODATA,Metric) # kg⋅kg⁻¹
1.000000016738611

julia> fluence(Conventional,Metric) # kg⋅kg⁻¹
1.000000195536555

julia> fluence(English,Metric) # kg⋅lb⁻¹
14.593902937206364
```
