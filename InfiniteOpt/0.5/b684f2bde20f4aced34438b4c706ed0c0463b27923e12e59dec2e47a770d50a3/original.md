```
JuMP.set_objective_coefficient(model::InfiniteModel,
                               variable::GeneralVariableRef,
                               coefficient::Real)::Nothing
```

Extend `JuMP.set_objective_coefficient` Set the linear objective coefficient  associated with `variable` to `coefficient`. Errors if the function type is  unsupported.

**Example**

```julia-repl
julia> @variable(model, x)
x

julia> @variable(model, y)
y

julia> @objective(model, x + y)
x + y

julia> set_objective_coefficient(model, y, 2)

julia> objective_function(model)
x + 2 y
```
