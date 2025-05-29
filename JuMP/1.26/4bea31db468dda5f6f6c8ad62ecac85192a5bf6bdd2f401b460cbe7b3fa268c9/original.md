```
coefficient(a::GenericAffExpr{C,V}, v::V) where {C,V}
```

Return the coefficient associated with variable `v` in the affine expression `a`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> expr = 2.0 * x + 1.0;

julia> coefficient(expr, x)
2.0
```
