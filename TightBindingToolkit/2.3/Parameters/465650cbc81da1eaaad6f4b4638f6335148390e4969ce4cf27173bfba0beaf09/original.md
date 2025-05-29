```julia
ModifyUnitCell!(uc::UnitCell, param::Param)
ModifyUnitCell!(uc::UnitCell, params::Vector{Param})
```

Modify all bonds in `UnitCell` corresponding to given `param`, taking the latest value in `param.value`. 
