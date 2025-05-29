```
coefficient(a::GenericQuadExpr{C,V}, v::V) where {C,V}
```

Return the coefficient associated with variable `v` in the affine component of `a`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> expr = 2.0 * x^2 + 3.0 * x;

julia> coefficient(expr, x)
3.0
```
