```
set_objective_coefficient(
    model::GenericModel,
    variable::GenericVariableRef,
    coefficient::Real,
)
```

Set the linear objective coefficient associated with `variable` to `coefficient`.

Note: this function will throw an error if a nonlinear objective is set.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @objective(model, Min, 2x + 1)
2 x + 1

julia> set_objective_coefficient(model, x, 3)

julia> objective_function(model)
3 x + 1
```
