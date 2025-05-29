```
wrap(o::Any, FM::Type{<:AbstractModel})
wrap(m::AbstractModel)
wrap(o::Any)::AbstractModel
```

This function wraps anything into an AbstractModel. The default behavior is the following:     - when called on an `AbstractModel`, the model is simply returned (no wrapping is         performed);     - Function`s and`FunctionWrapper`s are wrapped into a [`FunctionModel`](@ref);     - every other object is wrapped into a`ConstantModel`.

See also [`AbstractModel`](@ref), [`ConstantModel`](@ref), [`FunctionModel`](@ref), [`LeafModel`](@ref).
