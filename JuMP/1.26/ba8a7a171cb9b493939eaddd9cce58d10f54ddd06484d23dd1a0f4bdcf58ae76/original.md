```
get_attribute(
    model::Union{GenericModel,MOI.OptimizerWithAttributes},
    attr::Union{AbstractString,MOI.AbstractOptimizerAttribute},
)
```

Get the value of a solver-specifc attribute `attr`.

This is equivalent to calling [`MOI.get`](@ref) with the associated MOI model.

If `attr` is an `AbstractString`, it is converted to [`MOI.RawOptimizerAttribute`](@ref).

## Example

```jldoctest
julia> import HiGHS

julia> opt = optimizer_with_attributes(HiGHS.Optimizer, "output_flag" => true);

julia> model = Model(opt);

julia> get_attribute(model, "output_flag")
true

julia> get_attribute(model, MOI.RawOptimizerAttribute("output_flag"))
true

julia> get_attribute(opt, "output_flag")
true

julia> get_attribute(opt, MOI.RawOptimizerAttribute("output_flag"))
true
```
