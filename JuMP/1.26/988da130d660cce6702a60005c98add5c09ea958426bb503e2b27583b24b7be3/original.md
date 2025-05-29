```
set_optimizer_attributes(
    model::Union{GenericModel,MOI.OptimizerWithAttributes},
    pairs::Pair...,
)
```

Given a list of `attribute => value` pairs, calls `set_optimizer_attribute(model, attribute, value)` for each pair.

!!! compat
    This method will remain in all v1.X releases of JuMP, but it may be removed in a future v2.0 release. We recommend using [`set_attributes`](@ref) instead.


See also: [`set_optimizer_attribute`](@ref), [`get_optimizer_attribute`](@ref).

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> set_optimizer_attributes(model, "tol" => 1e-4, "max_iter" => 100)
```

is equivalent to:

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> set_optimizer_attribute(model, "tol", 1e-4)

julia> set_optimizer_attribute(model, "max_iter", 100)
```
