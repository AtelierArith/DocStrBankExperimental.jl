```
Model([optimizer_factory;] add_bridges::Bool = true)
```

Create a new instance of a JuMP model.

If `optimizer_factory` is provided, the model is initialized with thhe optimizer returned by `MOI.instantiate(optimizer_factory)`.

If `optimizer_factory` is not provided, use [`set_optimizer`](@ref) to set the optimizer before calling [`optimize!`](@ref).

If `add_bridges`, JuMP adds a [`MOI.Bridges.LazyBridgeOptimizer`](@ref) to automatically reformulate the problem into a form supported by the optimizer.

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> solver_name(model)
"Ipopt"

julia> import HiGHS

julia> import MultiObjectiveAlgorithms as MOA

julia> model = Model(() -> MOA.Optimizer(HiGHS.Optimizer); add_bridges = false);
```
