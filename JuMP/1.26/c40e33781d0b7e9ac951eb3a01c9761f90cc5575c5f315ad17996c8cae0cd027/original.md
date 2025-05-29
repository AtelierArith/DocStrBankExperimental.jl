```
reduced_cost(x::GenericVariableRef{T})::T where {T}
```

Return the reduced cost associated with variable `x`.

One interpretation of the reduced cost is that it is the change in the objective from an infinitesimal relaxation of the variable bounds.

This method is equivalent to querying the shadow price of the active variable bound (if one exists and is active).

See also: [`shadow_price`](@ref).

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x <= 1);

julia> @objective(model, Max, 2 * x + 1);

julia> optimize!(model)

julia> dual_status(model)
FEASIBLE_POINT::ResultStatusCode = 1

julia> reduced_cost(x)
2.0
```
