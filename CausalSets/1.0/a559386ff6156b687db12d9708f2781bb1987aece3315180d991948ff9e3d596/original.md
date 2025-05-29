```
bd_pointwise_pow(causet, i, field, dim, locality, ::Val{N}[, max_cardinality]) -> Float64
```

Calculate the `N`-th power pointwise BD operator, $B^N ϕ(e_i)$ on the field specified by `ϕ(e_j) = field[j]`.

The resulting value is given in units of the microscale $l$. In order to obtain a result in units of proper time, the return value of this function should thus be divided by $l^{2N}$.
