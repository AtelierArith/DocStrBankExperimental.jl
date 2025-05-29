```
capacity(n::Node)
capacity(n::Node, t)
```

Returns the capacity of a node `n` as `TimeProfile` or in operational period `t`.

!!! warning "Storage nodes"
    The capacity is not directly defined for [`Storage`](@ref) nodes. Instead, it is necessary to call the function on the respective field, see [`capacity(stor_par::AbstractStorageParameters)`](@ref).

