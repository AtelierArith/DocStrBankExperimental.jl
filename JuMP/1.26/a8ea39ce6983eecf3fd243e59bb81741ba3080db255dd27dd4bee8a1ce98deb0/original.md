```
node_count(model::GenericModel)
```

If available, returns the total number of branch-and-bound nodes explored during the most recent optimization in a Mixed Integer Program (the [`MOI.NodeCount`](@ref) attribute).

Throws a `MOI.GetAttributeNotAllowed` error if the attribute is not implemented by the solver.

## Example

```jldoctest; filter=r"[0-9].+"
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> optimize!(model)

julia> node_count(model)
0
```
