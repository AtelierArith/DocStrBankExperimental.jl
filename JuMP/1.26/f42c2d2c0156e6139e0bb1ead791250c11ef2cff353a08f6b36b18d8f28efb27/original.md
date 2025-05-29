```
relative_gap(model::GenericModel)
```

Return the final relative optimality gap after a call to `optimize!(model)`.

Exact value depends upon implementation of [`MOI.RelativeGap`](@ref) by the particular solver used for optimization.

This function is equivalent to querying the [`MOI.RelativeGap`](@ref) attribute.

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 1, Int);

julia> @objective(model, Min, 2 * x + 1);

julia> optimize!(model)

julia> relative_gap(model)
0.0
```
