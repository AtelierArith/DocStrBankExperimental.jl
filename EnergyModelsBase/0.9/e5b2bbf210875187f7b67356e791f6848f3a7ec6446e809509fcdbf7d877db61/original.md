```
opex_fixed(n::Node)
opex_fixed(n::Node, t_inv)
```

Returns the fixed OPEX of a node node `n` as `TimeProfile` or in strategic period `t_inv`.

!!! warning "Storage nodes"
    The fixed OPEX is not directly defined for [`Storage`](@ref) nodes. Instead, it is necessary to call the function on the respective field, see [`opex_fixed(stor_par::AbstractStorageParameters)`](@ref).

