```
set_objective_coefficient(
    model::GenericModel{T},
    variables_1::AbstractVector{<:GenericVariableRef{T}},
    variables_2::AbstractVector{<:GenericVariableRef{T}},
    coefficients::AbstractVector{<:Real},
) where {T}
```

Set multiple quadratic objective coefficients associated with `variables_1` and `variables_2` to `coefficients`, in a single call.

Note: this function will throw an error if a nonlinear objective is set.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> @objective(model, Min, x[1]^2 + x[1] * x[2])
x[1]² + x[1]*x[2]

julia> set_objective_coefficient(model, [x[1], x[1]], [x[1], x[2]], [2, 3])

julia> objective_function(model)
2 x[1]² + 3 x[1]*x[2]
```
