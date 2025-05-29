```Julia
specificity(U::UnitSystem,S::UnitSystem) = volume(U,S)/molaramount(U,S)/time(U,S)
specificity(v::Real,U::UnitSystem,S::UnitSystem) = v/specificity(U,S)
```

触媒効率または `volume` per `mole` per `time` (m³⋅mol⁻¹⋅s⁻¹)、単位換算係数。

```Julia
julia> specificity(CGS,Metric) # m³⋅cm⁻³
1.0000000000000006e-6

julia> specificity(English,Metric) # m³⋅lb-mol⋅mol⁻¹⋅ft⁻³
6.242796057614462e-5
```
