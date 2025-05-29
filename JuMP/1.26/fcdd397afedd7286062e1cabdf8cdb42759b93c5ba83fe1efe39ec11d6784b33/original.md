```
constant(aff::GenericAffExpr{C,V})::C
```

Return the constant of the affine expression.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> aff = 2.0 * x + 3.0;

julia> constant(aff)
3.0
```
