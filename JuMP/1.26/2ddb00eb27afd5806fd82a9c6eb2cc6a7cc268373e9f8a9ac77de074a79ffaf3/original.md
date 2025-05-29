```
bridge_constraints(model::GenericModel)
```

When in direct mode, return `false`.

When in manual or automatic mode, return a `Bool` indicating whether the optimizer is set and unsupported constraints are automatically bridged to equivalent supported constraints when an appropriate transformation is available.

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> bridge_constraints(model)
true

julia> model = Model(Ipopt.Optimizer; add_bridges = false);

julia> bridge_constraints(model)
false
```
