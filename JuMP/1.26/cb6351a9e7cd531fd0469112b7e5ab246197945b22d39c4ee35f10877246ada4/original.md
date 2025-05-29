```
op_ifelse(a, x, y)
```

A function that falls back to `ifelse(a, x, y)`, but when called with a JuMP variables or expression in the first argument, returns a [`GenericNonlinearExpr`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> op_ifelse(true, 1.0, 2.0)
1.0

julia> op_ifelse(x, 1.0, 2.0)
ifelse(x, 1.0, 2.0)

julia> op_ifelse(true, x, 2.0)
x
```
