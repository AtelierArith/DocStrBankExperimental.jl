```
drop_zeros!(expr::GenericAffExpr)
```

Remove terms in the affine expression with `0` coefficients.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> expr = x[1] + x[2];

julia> add_to_expression!(expr, -1.0, x[1])
0 x[1] + x[2]

julia> drop_zeros!(expr)

julia> expr
x[2]
```
