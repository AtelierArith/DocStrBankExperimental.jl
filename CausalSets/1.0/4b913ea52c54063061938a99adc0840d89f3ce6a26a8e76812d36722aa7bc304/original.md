```
bd_pointwise(causet, i, field, dim, locality[, max_cardinality]) -> Float64
```

Calculate the pointwise BD operator $B ϕ(e_i)$ on the field specified by `ϕ(e_j) = field[j]`.

The resulting value is given in units of the microscale $l$. In order to obtain a result in units of proper time, the return value of this function should thus be divided by $l^2$.
