```
optimizer_index(x::GenericVariableRef)::MOI.VariableIndex
optimizer_index(x::ConstraintRef{<:GenericModel})::MOI.ConstraintIndex
```

Return the variable or constraint index that corresponds to `x` in the associated model `unsafe_backend(owner_model(x))`.

This function should be used with [`unsafe_backend`](@ref).

As a safer alternative, use [`backend`](@ref) and [`index`](@ref). See the docstrings of [`backend`](@ref) and [`unsafe_backend`](@ref) for more details.

## Throws

  * Throws [`NoOptimizer`](@ref) if no optimizer is set.
  * Throws an `ErrorException` if the optimizer is set but is not attached.
  * Throws an `ErrorException` if the index is bridged.

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 0)
x

julia> MOI.Utilities.attach_optimizer(model)

julia> highs = unsafe_backend(model)
A HiGHS model with 1 columns and 0 rows.

julia> optimizer_index(x)
MOI.VariableIndex(1)
```
