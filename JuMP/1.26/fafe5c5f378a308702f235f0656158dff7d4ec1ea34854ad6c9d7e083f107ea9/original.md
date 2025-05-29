```
has_duals(model::GenericModel; result::Int = 1)
```

Return `true` if the solver has a dual solution in result index `result` available to query, otherwise return `false`.

See also [`dual`](@ref), [`shadow_price`](@ref), and [`result_count`](@ref).

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x);

julia> @constraint(model, c, x <= 1)
c : x ≤ 1

julia> @objective(model, Max, 2 * x + 1);

julia> has_duals(model)
false

julia> optimize!(model)

julia> has_duals(model)
true
```
