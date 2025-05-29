```julia
ModifyFields!(uc::UnitCell, site::Int64, newField::Vector{Float64})
ModifyFields!(uc::UnitCell, newField::Vector{Vector{Float64}})
```

Modify the on-site fields in the `UnitCell`, either one at a time, or all of them.
