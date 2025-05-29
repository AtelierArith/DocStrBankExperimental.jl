```
SkipModelConvertScalarSetWrapper(set::MOI.AbstractScalarSet)
```

JuMP uses [`model_convert`](@ref) to automatically promote [`MOI.AbstractScalarSet`](@ref) sets to the same [`value_type`](@ref) as the model.

In cases there this is undesirable, wrap the set in `SkipModelConvertScalarSetWrapper` to pass the set un-changed to the solver.

!!! warning
    This struct is intended for use internally by JuMP extensions. You should not need to use it in regular JuMP code.


## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, x in MOI.EqualTo(1 // 2))
x = 0.5

julia> @constraint(model, x in SkipModelConvertScalarSetWrapper(MOI.EqualTo(1 // 2)))
x = 1//2
```
