```
objective_bound(model::GenericModel)
```

Return the best known bound on the optimal objective value after a call to `optimize!(model)`.

For scalar-valued objectives, this function returns a `Float64`. For vector-valued objectives, it returns a `Vector{Float64}`.

In the case of a vector-valued objective, this returns the *ideal point*, that is, the point obtained if each objective was optimized independently.

This function is equivalent to querying the [`MOI.ObjectiveBound`](@ref) attribute.

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 1, Int);

julia> @objective(model, Min, 2 * x + 1);

julia> optimize!(model)

julia> objective_bound(model)
3.0
```
