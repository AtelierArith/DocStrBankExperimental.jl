```
solve_time(model::GenericModel)
```

If available, returns the solve time in wall-clock seconds reported by the solver (the [`MOI.SolveTimeSec`](@ref) attribute).

Throws a `MOI.GetAttributeNotAllowed` error if the attribute is not implemented by the solver.

## Example

```jldoctest; filter=r"[0-9].+"
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> optimize!(model)

julia> solve_time(model)
1.0488089174032211e-5
```
