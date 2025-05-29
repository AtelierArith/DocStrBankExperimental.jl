```
primal_status(model::GenericModel; result::Int = 1)
```

Return a [`MOI.ResultStatusCode`](@ref) describing the status of the most recent primal solution of the solver (that is, the [`MOI.PrimalStatus`](@ref) attribute) associated with the result index `result`.

See also: [`result_count`](@ref).

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> primal_status(model; result = 2)
NO_SOLUTION::ResultStatusCode = 0
```
