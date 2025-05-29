```
set_optimizer_attribute(
    model::Union{GenericModel,MOI.OptimizerWithAttributes},
    attr::Union{AbstractString,MOI.AbstractOptimizerAttribute},
    value,
)
```

Set the solver-specific attribute `attr` in `model` to `value`.

If `attr` is an `AbstractString`, this is equivalent to `set_optimizer_attribute(model, MOI.RawOptimizerAttribute(name), value)`.

!!! compat
    This method will remain in all v1.X releases of JuMP, but it may be removed in a future v2.0 release. We recommend using [`set_attribute`](@ref) instead.


See also: [`set_optimizer_attributes`](@ref), [`get_optimizer_attribute`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> set_optimizer_attribute(model, MOI.Silent(), true)
```
