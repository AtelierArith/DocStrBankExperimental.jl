```
coefficient(a::GenericQuadExpr{C,V}, v1::V, v2::V) where {C,V}
```

Return the coefficient associated with the term `v1 * v2` in the quadratic expression `a`.

Note that `coefficient(a, v1, v2)` is the same as `coefficient(a, v2, v1)`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> expr = 2.0 * x[1] * x[2];

julia> coefficient(expr, x[1], x[2])
2.0

julia> coefficient(expr, x[2], x[1])
2.0

julia> coefficient(expr, x[1], x[1])
0.0
```
