```Julia
viscosity(U::UnitSystem,S::UnitSystem) = inertia(U,S)/length(U,S)/time(U,S)
viscosity(v::Real,U::UnitSystem,S::UnitSystem) = v/viscosity(U,S)
```

変形に対する抵抗または `viscosity` (Pa⋅s, kg⋅m⁻¹⋅s⁻¹)、単位変換係数。

```Julia
julia> viscosity(CGS,Metric) # Pa⋅Ba⁻¹
0.09999999999999998

julia> viscosity(English,Metric) # Pa⋅ft²⋅lb⁻¹
47.88025898033583

julia> viscosity(British,Metric) # Pa⋅ft²⋅lb⁻¹
47.880258980335825
```
