```julia
create_poly_cost(
    gen,
    cost_colnames
) -> Union{Tuple{InfrastructureSystems.LinearCurve, Float64}, Tuple{InfrastructureSystems.QuadraticCurve, Float64}}

```

```
create_poly_cost(gen, cost_colnames)
```

Return a Polynomial function cost based on the coeffiecients provided on gen.

Three supported cases,

1. If three values are passed then we have data looking like: `a2 * x^2 + a1 * x + a0`,
2. If `a1` and `a0` are passed then we have data looking like: `a1 * x + a0`,
3. If only `a1` is passed then we have data looking like: `a1 * x`.
