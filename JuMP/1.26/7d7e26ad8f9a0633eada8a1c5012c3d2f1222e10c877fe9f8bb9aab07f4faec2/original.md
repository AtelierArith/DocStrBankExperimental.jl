```
solver_name(model::GenericModel)
```

If available, returns the [`MOI.SolverName`](@ref) property of the underlying optimizer.

Returns `"No optimizer attached."` in `AUTOMATIC` or `MANUAL` modes when no optimizer is attached.

Returns `"SolverName() attribute not implemented by the optimizer."` if the attribute is not implemented.

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> solver_name(model)
"Ipopt"

julia> model = Model();

julia> solver_name(model)
"No optimizer attached."

julia> model = Model(MOI.FileFormats.MPS.Model);

julia> solver_name(model)
"SolverName() attribute not implemented by the optimizer."
```
