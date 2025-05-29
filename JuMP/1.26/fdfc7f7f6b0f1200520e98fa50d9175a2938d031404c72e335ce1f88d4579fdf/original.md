```
set_silent(model::GenericModel)
```

Takes precedence over any other attribute controlling verbosity and requires the solver to produce no output.

See also: [`unset_silent`](@ref).

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> set_silent(model)

julia> get_attribute(model, MOI.Silent())
true

julia> unset_silent(model)

julia> get_attribute(model, MOI.Silent())
false
```
