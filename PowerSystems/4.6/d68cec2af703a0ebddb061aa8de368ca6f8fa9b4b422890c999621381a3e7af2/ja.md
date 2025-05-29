```julia
create_poly_cost(
    gen,
    cost_colnames
) -> Union{Tuple{InfrastructureSystems.LinearCurve, Float64}, Tuple{InfrastructureSystems.QuadraticCurve, Float64}}

```

```
create_poly_cost(gen, cost_colnames)
```

提供された係数に基づいて多項式関数のコストを返します。

サポートされているケースは3つあります。

1. 3つの値が渡されると、データは次のようになります: `a2 * x^2 + a1 * x + a0`,
2. `a1`と`a0`が渡されると、データは次のようになります: `a1 * x + a0`,
3. `a1`のみが渡されると、データは次のようになります: `a1 * x`.
