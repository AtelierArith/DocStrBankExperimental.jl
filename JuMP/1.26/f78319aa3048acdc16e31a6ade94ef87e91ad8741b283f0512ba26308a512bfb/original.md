```
barrier_iterations(model::GenericModel)
```

If available, returns the cumulative number of barrier iterations during the most-recent optimization (the [`MOI.BarrierIterations`](@ref) attribute).

Throws a `MOI.GetAttributeNotAllowed` error if the attribute is not implemented by the solver.

## Example

```jldoctest; filter=r"[0-9].+"
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> optimize!(model)

julia> barrier_iterations(model)
0
```
