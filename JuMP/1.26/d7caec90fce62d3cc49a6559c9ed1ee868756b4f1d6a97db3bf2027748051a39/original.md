```
dual(con_ref::ConstraintRef; result::Int = 1)
```

Return the dual value of constraint `con_ref` associated with result index `result` of the most-recent solution returned by the solver.

Use [`dual_status`](@ref) to check if a result exists before asking for values.

See also: [`result_count`](@ref), [`shadow_price`](@ref).

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x);

julia> @constraint(model, c, x <= 1)
c : x ≤ 1

julia> @objective(model, Max, 2 * x + 1);

julia> optimize!(model)

julia> dual_status(model)
FEASIBLE_POINT::ResultStatusCode = 1

julia> dual(c)
-2.0
```
