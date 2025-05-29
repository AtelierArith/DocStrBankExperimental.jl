```Julia
angularlength(U::UnitSystem,S::UnitSystem) = length(U,S)/angle(U,S)
angularlength(v::Real,U::UnitSystem,S::UnitSystem) = v/angularlength(U,S)
```

単位 `length` あたりの `angle` (m⋅rad⁻¹)、単位変換係数。

```Julia
julia> angularlength(CGS,Metric) # cm⋅m⁻¹
0.010000000000000002

julia> angularlength(English,Metric) # ft⋅m⁻¹
0.3048
```
