```
opex_fixed(stor_par::UnionOpexFixed)
opex_fixed(stor_par::UnionOpexFixed, t_inv)
```

Returns the fixed OPEX of storage parameter `stor_par` as `TimeProfile` or in strategic period `t_inv`.

!!! note "Accessing storage parameters"
    The individual storage parameters of a [`Storage`](@ref) node can be accessed through the functions [`charge(n)`](@ref), [`level(n)`](@ref), and [`discharge(n)`](@ref).

