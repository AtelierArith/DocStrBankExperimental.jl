```
termination_status(model::GenericModel)
```

Return a [`MOI.TerminationStatusCode`](@ref) describing why the solver stopped (that is, the [`MOI.TerminationStatus`](@ref) attribute).

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> termination_status(model)
OPTIMIZE_NOT_CALLED::TerminationStatusCode = 0
```
