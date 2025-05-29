```
op_strictly_greater_than(x, y)
```

A function that falls back to `x > y`, but when called with JuMP variables or expressions, returns a [`GenericNonlinearExpr`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> op_strictly_greater_than(1, 2)
false

julia> op_strictly_greater_than(x, 2)
x > 2
```
