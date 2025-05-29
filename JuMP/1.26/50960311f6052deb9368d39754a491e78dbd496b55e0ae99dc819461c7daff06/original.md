```
simplex_iterations(model::GenericModel)
```

If available, returns the cumulative number of simplex iterations during the most-recent optimization (the [`MOI.SimplexIterations`](@ref) attribute).

Throws a `MOI.GetAttributeNotAllowed` error if the attribute is not implemented by the solver.

## Example

```jldoctest; filter=r"[0-9].+"
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> optimize!(model)

julia> simplex_iterations(model)
0
```
