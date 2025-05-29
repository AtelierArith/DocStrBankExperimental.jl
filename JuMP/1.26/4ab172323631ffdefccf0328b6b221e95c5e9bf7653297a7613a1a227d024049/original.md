```
unset_silent(model::GenericModel)
```

Neutralize the effect of the `set_silent` function and let the solver attributes control the verbosity.

See also: [`set_silent`](@ref).

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
