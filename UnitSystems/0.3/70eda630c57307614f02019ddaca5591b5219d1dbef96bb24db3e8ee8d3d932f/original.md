```Julia
rotationalinertia(U::UnitSystem,S::UnitSystem) = mass(U,S)*area(U,S)
rotationalinertia(v::Real,U::UnitSystem,S::UnitSystem) = v/rotationalinertia(U,S)
```

Moment of inertia or `rotationalinertia` (kg⋅m²), unit conversion factor.

```Julia
julia> rotationalinertia(CGS,Metric) # kg⋅m²⋅g⁻¹⋅cm⁻²
1.0000000000000005e-7

julia> rotationalinertia(CGS,British) # slug⋅ft²⋅g⁻¹⋅cm⁻²
7.375621492772654e-8

julia> rotationalinertia(English,Metric) # kg⋅m²⋅lb⁻¹⋅ft⁻²
0.042140110093804806
```
