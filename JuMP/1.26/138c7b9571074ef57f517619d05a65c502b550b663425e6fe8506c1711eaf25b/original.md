```
get_optimizer_attribute(
    model::Union{GenericModel,MOI.OptimizerWithAttributes},
    attr::Union{AbstractString,MOI.AbstractOptimizerAttribute},
)
```

Return the value associated with the solver-specific attribute `attr`.

If `attr` is an `AbstractString`, this is equivalent to `get_optimizer_attribute(model, MOI.RawOptimizerAttribute(name))`.

!!! compat
    This method will remain in all v1.X releases of JuMP, but it may be removed in a future v2.0 release. We recommend using [`get_attribute`](@ref) instead.


See also: [`set_optimizer_attribute`](@ref), [`set_optimizer_attributes`](@ref).

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> get_optimizer_attribute(model, MOI.Silent())
false
```
