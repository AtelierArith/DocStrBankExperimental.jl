```
set_objective_coefficient(
    model::GenericModel{T},
    variable_1::GenericVariableRef{T},
    variable_2::GenericVariableRef{T},
    coefficient::Real,
) where {T}
```

Set the quadratic objective coefficient associated with `variable_1` and `variable_2` to `coefficient`.

Note: this function will throw an error if a nonlinear objective is set.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> @objective(model, Min, x[1]^2 + x[1] * x[2])
x[1]² + x[1]*x[2]

julia> set_objective_coefficient(model, x[1], x[1], 2)

julia> set_objective_coefficient(model, x[1], x[2], 3)

julia> objective_function(model)
2 x[1]² + 3 x[1]*x[2]
```
