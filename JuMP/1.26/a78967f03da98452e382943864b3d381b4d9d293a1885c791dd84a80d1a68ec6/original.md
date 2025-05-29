```
objective_value(model::GenericModel; result::Int = 1)
```

Return the objective value associated with result index `result` of the most-recent solution returned by the solver.

For scalar-valued objectives, this function returns a `Float64`. For vector-valued objectives, it returns a `Vector{Float64}`.

This function is equivalent to querying the [`MOI.ObjectiveValue`](@ref) attribute.

See also: [`result_count`](@ref).

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 1);

julia> @objective(model, Min, 2 * x + 1);

julia> optimize!(model)

julia> objective_value(model)
3.0

julia> objective_value(model; result = 2)
ERROR: Result index of attribute MathOptInterface.ObjectiveValue(2) out of bounds. There are currently 1 solution(s) in the model.
Stacktrace:
[...]
```
