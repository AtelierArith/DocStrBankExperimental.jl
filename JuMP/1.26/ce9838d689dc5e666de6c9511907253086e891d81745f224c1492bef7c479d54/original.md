```
set_time_limit_sec(model::GenericModel, limit::Float64)
```

Set the time limit (in seconds) of the solver.

Can be unset using [`unset_time_limit_sec`](@ref) or with `limit` set to `nothing`.

See also: [`unset_time_limit_sec`](@ref), [`time_limit_sec`](@ref).

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> time_limit_sec(model)

julia> set_time_limit_sec(model, 60.0)

julia> time_limit_sec(model)
60.0

julia> unset_time_limit_sec(model)

julia> time_limit_sec(model)
```
