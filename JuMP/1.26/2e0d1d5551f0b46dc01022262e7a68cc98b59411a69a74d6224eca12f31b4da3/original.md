```
dual_objective_value(model::GenericModel; result::Int = 1)
```

Return the value of the objective of the dual problem associated with result index `result` of the most-recent solution returned by the solver.

Throws `MOI.UnsupportedAttribute{MOI.DualObjectiveValue}` if the solver does not support this attribute.

This function is equivalent to querying the [`MOI.DualObjectiveValue`](@ref) attribute.

See also: [`result_count`](@ref).

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 1);

julia> @objective(model, Min, 2 * x + 1);

julia> optimize!(model)

julia> dual_objective_value(model)
3.0

julia> dual_objective_value(model; result = 2)
ERROR: Result index of attribute MathOptInterface.DualObjectiveValue(2) out of bounds. There are currently 1 solution(s) in the model.
Stacktrace:
[...]
```
