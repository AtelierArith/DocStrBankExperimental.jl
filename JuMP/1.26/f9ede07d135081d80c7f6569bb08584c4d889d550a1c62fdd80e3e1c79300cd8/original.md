```
op_equal_to(x, y)
```

A function that falls back to `x == y`, but when called with JuMP variables or expressions, returns a [`GenericNonlinearExpr`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> op_equal_to(2, 2)
true

julia> op_equal_to(x, 2)
x == 2
```
