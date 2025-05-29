```
set_objective_coefficient(
    model::GenericModel,
    variables::Vector{<:GenericVariableRef},
    coefficients::Vector{<:Real},
)
```

Set multiple linear objective coefficients associated with `variables` to `coefficients`, in a single call.

Note: this function will throw an error if a nonlinear objective is set.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @variable(model, y);

julia> @objective(model, Min, 3x + 2y + 1)
3 x + 2 y + 1

julia> set_objective_coefficient(model, [x, y], [5, 4])

julia> objective_function(model)
5 x + 4 y + 1
```
