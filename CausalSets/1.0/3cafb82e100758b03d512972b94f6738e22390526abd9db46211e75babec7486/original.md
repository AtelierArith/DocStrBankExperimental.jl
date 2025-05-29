```
bd_integrated_pow(abundances::Vector{Int64}, dim::Int64, locality::BDLocality[, max_cardinality])
```

Calculate the integrated Benincasa-Dowker operator from the abundances vector `abundances`.

The resulting value is given in units of the microscale $l$. In order to obtain a result in units of proper time, the return value of this function should thus be divided by $l^2$.
