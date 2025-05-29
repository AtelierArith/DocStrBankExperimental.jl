```
time_limit_sec(model::GenericModel)
```

Return the time limit (in seconds) of the `model`.

Returns `nothing` if unset.

See also: [`set_time_limit_sec`](@ref), [`unset_time_limit_sec`](@ref).

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
