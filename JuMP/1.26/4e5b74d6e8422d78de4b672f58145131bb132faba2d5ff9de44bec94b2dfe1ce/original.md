```
set_attribute(
    model::Union{GenericModel,MOI.OptimizerWithAttributes},
    attr::Union{AbstractString,MOI.AbstractOptimizerAttribute},
    value,
)
```

Set the value of a solver-specifc attribute `attr` to `value`.

This is equivalent to calling [`MOI.set`](@ref) with the associated MOI model.

If `attr` is an `AbstractString`, it is converted to [`MOI.RawOptimizerAttribute`](@ref).

## Example

```jldoctest
julia> import HiGHS

julia> opt = optimizer_with_attributes(HiGHS.Optimizer, "output_flag" => false);

julia> model = Model(opt);

julia> set_attribute(model, "output_flag", false)

julia> set_attribute(model, MOI.RawOptimizerAttribute("output_flag"), true)

julia> set_attribute(opt, "output_flag", true)

julia> set_attribute(opt, MOI.RawOptimizerAttribute("output_flag"), false)
```
