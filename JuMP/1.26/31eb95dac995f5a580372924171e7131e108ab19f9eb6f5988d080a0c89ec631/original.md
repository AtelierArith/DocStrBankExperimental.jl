```
optimize!(
    model::GenericModel;
    ignore_optimize_hook = (model.optimize_hook === nothing),
    kwargs...,
)
```

Optimize the model.

If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a [`NoOptimizer`](@ref) error is thrown.

If `ignore_optimize_hook == true`, the optimize hook is ignored and the model is solved as if the hook was not set. Keyword arguments `kwargs` are passed to the `optimize_hook`. An error is thrown if `optimize_hook` is `nothing` and keyword arguments are provided.

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> function my_optimize_hook(model; foo)
           println("Hook called with foo = ", foo)
           return optimize!(model; ignore_optimize_hook = true)
       end
my_optimize_hook (generic function with 1 method)

julia> set_optimize_hook(model, my_optimize_hook)
my_optimize_hook (generic function with 1 method)

julia> optimize!(model; foo = 2)
Hook called with foo = 2
```
