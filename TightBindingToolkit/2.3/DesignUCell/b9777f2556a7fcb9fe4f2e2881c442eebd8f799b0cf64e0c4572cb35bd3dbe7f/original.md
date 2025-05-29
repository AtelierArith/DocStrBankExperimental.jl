```julia
ModifyIsotropicFields!(uc::UnitCell, newField::Vector{Float64})
ModifyIsotropicFields!(uc::UnitCell, newField::Float64, dim::Int64)
```

Modify the on site field uniformly, on all sublattices. The optional argument `dim` is if you want to only modify one of the 4 elements of on-site fields (3 Zeeman and 1 chemical potential).
