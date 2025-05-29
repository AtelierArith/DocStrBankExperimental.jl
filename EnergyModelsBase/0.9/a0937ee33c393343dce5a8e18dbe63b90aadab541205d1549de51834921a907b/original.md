```
opex_var(stor_par::UnionOpexVar)
opex_var(stor_par::UnionOpexVar, t)
```

Returns the variable OPEX of storage parameter `stor_par` as `TimeProfile` or in operational period `t`.

!!! note "Accessing storage parameters"
    The individual storage parameters of a [`Storage`](@ref) node can be accessed through the functions [`charge(n)`](@ref), [`level(n)`](@ref), and [`discharge(n)`](@ref).

