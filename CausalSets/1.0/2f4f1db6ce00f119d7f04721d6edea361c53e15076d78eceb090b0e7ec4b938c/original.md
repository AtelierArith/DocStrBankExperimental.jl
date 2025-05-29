```
bd_integrated_pow(abundances::Array{Int64, N}, dim::Int64, locality::BDLocality, ::Val{N}[, max_cardinality])
```

Calculate the integrated `N`-th power of the Benincasa-Dowker operator from the abundances array `abundances`.

The resulting value is given in units of the microscale $l$. In order to obtain a result in units of proper time, the return value of this function should thus be divided by $l^{2N}$.
