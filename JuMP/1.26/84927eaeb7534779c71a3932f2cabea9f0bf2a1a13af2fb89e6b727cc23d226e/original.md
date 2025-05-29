```
constant(quad::GenericQuadExpr{C,V})::C
```

Return the constant of the quadratic expression.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> quad = 2.0 * x^2 + 3.0;

julia> constant(quad)
3.0
```
