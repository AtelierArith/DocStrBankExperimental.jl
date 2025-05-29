```
set_optimizer(
    model::GenericModel,
    optimizer_factory;
    add_bridges::Bool = true,
    kwargs...,
)
```

Creates an empty [`MOI.AbstractOptimizer`](@ref) instance by calling [`MOI.instantiate`](@ref) on `optimizer_factory` and sets it as the optimizer of `model`.

Specifically, `optimizer_factory` must be callable with zero arguments and return an empty [`MOI.AbstractOptimizer`](@ref).

If `add_bridges` is true, constraints and objectives that are not supported by the optimizer are automatically bridged to equivalent supported formulation. Passing `add_bridges = false` can improve performance if the solver natively supports all of the elements in `model`.

Additional `kwargs` are passed to [`MOI.instantiate`](@ref).

See [`set_attribute`](@ref) for setting solver-specific parameters of the optimizer.

## Example

```jldoctest
julia> import HiGHS

julia> model = Model();

julia> set_optimizer(model, () -> HiGHS.Optimizer())

julia> set_optimizer(model, HiGHS.Optimizer; add_bridges = false)
```
