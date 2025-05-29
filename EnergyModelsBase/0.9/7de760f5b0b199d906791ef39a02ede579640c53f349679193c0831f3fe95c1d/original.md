```
opex_var(n::Node)
opex_var(n::Node, t)
```

Returns the variable OPEX of a node `n` as `TimeProfile` or in operational period `t`.

!!! warning "Storage nodes"
    The variable OPEX is not directly defined for [`Storage`](@ref) nodes. Instead, it is necessary to call the function on the respective field, see [`opex_var(stor_par::AbstractStorageParameters)`](@ref).

