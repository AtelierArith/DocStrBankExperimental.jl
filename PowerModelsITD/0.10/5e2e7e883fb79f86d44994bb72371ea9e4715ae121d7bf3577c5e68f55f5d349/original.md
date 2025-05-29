```
function assign_boundary_buses!(
    data::Dict{String,<:Any};
    multinetwork::Bool=false
)
```

Assigns the names given in the boundary linking data to number buses in corresponding transmission and distribution networks. `data` is the pmitd dictionary containing the boundary information and `multinetwork` is the boolean that defines if there are multinetwork boundary buses to be assigned.
