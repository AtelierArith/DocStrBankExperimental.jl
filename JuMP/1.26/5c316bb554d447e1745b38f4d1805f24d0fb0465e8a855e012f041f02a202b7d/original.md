```
op_or(x, y)
```

A function that falls back to `x | y`, but when called with JuMP variables or expressions, returns a [`GenericNonlinearExpr`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> op_or(true, false)
true

julia> op_or(true, x)
true || x
```
