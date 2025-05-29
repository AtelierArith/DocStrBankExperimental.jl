```
@expressions(model, args...)
```

Adds multiple expressions to model at once, in the same fashion as the [`@expression`](@ref) macro.

The model must be the first argument, and multiple expressions can be added on multiple lines wrapped in a `begin ... end` block.

The macro returns a tuple containing the expressions that were defined.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @variable(model, y);

julia> @variable(model, z[1:2]);

julia> a = [4, 5];

julia> @expressions(model, begin
           my_expr, x^2 + y^2
           my_expr_1[i = 1:2], a[i] - z[i]
       end)
(x² + y², AffExpr[-z[1] + 4, -z[2] + 5])
```
