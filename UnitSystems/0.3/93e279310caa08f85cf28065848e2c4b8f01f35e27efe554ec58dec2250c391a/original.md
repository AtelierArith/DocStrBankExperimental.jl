```Julia
specificweight(U::UnitSystem,S::UnitSystem) = force(U,S)/volume(U,S)
specificweight(v::Real,U::UnitSystem,S::UnitSystem) = v/specificweight(U,S)
```

Specific weight or `force` per `volume` (N⋅m⁻³ or lb⋅ft⁻³), unit conversion factor.

```Julia
julia> specificweight(CGS,Metric) # N⋅cm³⋅dyn⁻¹⋅m⁻³
9.999999999999995

julia> specificweight(CGS,Brtish) # lb⋅cm³⋅dyn⁻¹⋅ft⁻³
0.06365880354264161

julia> specificweight(English,Metric) # N⋅ft³⋅lb⁻¹⋅m⁻³
157.08746384624618
```
