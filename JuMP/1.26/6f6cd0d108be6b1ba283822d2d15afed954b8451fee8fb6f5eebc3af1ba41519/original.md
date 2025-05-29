```
GenericModel{T}([optimizer_factory]; kwargs...) where {T<:Real}
```

Create a new instance of a JuMP model.

If `optimizer_factory` is provided, the model is initialized with the optimizer using `set_optimizer(model, optimizer_factory; kwargs...)`. See [`set_optimizer`](@ref) for details on `kwargs`.

If `optimizer_factory` is not provided, use [`set_optimizer`](@ref) to set the optimizer before calling [`optimize!`](@ref).

## Value type `T`

Passing a type other than `Float64` as the value type `T` is an advanced operation. The value type must match that expected by the chosen optimizer. Consult the optimizers documentation for details.

If not documented, assume that the optimizer supports only `Float64`.

Choosing an unsupported value type will throw an [`MOI.UnsupportedConstraint`](@ref) or an [`MOI.UnsupportedAttribute`](@ref) error, the timing of which (during the model construction or during a call to [`optimize!`](@ref)) depends on how the solver is interfaced to JuMP.

## Example

```jldoctest
julia> model = GenericModel{BigFloat}();

julia> typeof(model)
GenericModel{BigFloat}
```
