```
set_optimizer(
    model::Model,
    optimizer_factory;
    add_bridges::Bool = true,
)
```

Creates an empty `MathOptInterface.AbstractOptimizer` instance by calling `optimizer_factory()` and sets it as the optimizer of `model`. Specifically, `optimizer_factory` must be callable with zero arguments and return an empty `MathOptInterface.AbstractOptimizer`.

If `add_bridges` is true, constraints and objectives that are not supported by the optimizer are automatically bridged to equivalent supported formulation. Passing `add_bridges = false` can improve performance if the solver natively supports all of the elements in `model`.

See [`set_optimizer_attributes`](@ref) and [`set_optimizer_attribute`](@ref) for setting solver-specific parameters of the optimizer.

## Examples

```julia
model = Model()
set_optimizer(model, HiGHS.Optimizer)
set_optimizer(model, HiGHS.Optimizer; add_bridges = false)
```
