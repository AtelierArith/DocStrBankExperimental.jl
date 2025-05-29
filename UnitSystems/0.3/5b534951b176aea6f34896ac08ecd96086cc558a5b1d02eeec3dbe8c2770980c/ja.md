```Julia
specificforce(U::UnitSystem,S::UnitSystem) = acceleration(U,S)/gravity(U,S)
specificforce(v::Real,U::UnitSystem,S::UnitSystem) = v/specificforce(U,S)
```

重力または `力` あたりの `質量` または `gforce` (N/kg, m⋅s⁻²)、単位変換係数。

```Julia
julia> specificforce(CGS,Metric)
0.01

julia> specificforce(Engineering,Metric)
9.80665

julia> specificforce(English,Metric)
9.80665
```
