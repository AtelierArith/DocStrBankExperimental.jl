```
set_objective_function(model::GenericModel, func::MOI.AbstractFunction)
set_objective_function(model::GenericModel, func::AbstractJuMPScalar)
set_objective_function(model::GenericModel, func::Real)
set_objective_function(model::GenericModel, func::Vector{<:AbstractJuMPScalar})
```

Set the objective function of `model` to the given function `func`.

See also: [`@objective`](@ref), [`set_objective_function`](@ref), [`set_objective`](@ref)

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @objective(model, Min, x);

julia> objective_function(model)
x

julia> set_objective_function(model, 2 * x + 1)

julia> objective_function(model)
2 x + 1
```
