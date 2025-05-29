```Julia
molarity(U::UnitSystem,S::UnitSystem) = molaramount(U,S)/volume(U,S)
molarity(v::Real,U::UnitSystem,S::UnitSystem) = v/molarity(U,S)
```

モル濃度または `molaramount` あたりの `volume` (mol⋅m⁻³)、単位変換係数。

```Julia
julia> molarity(CGS,Metric) # cm³⋅m⁻³
999999.9999999994

julia> molarity(English,SI2019) # ft³⋅m⁻³
16018.463379466388
```
