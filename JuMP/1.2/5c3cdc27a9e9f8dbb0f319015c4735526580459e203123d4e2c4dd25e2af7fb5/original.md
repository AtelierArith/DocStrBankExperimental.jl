```
set_optimize_hook(model::Model, f::Union{Function,Nothing})
```

Set the function `f` as the optimize hook for `model`.

`f` should have a signature `f(model::Model; kwargs...)`, where the `kwargs` are those passed to [`optimize!`](@ref).

## Notes

  * The optimize hook should generally modify the model, or some external state in some way, and then call `optimize!(model; ignore_optimize_hook = true)` to optimize the problem, bypassing the hook.
  * Use `set_optimize_hook(model, nothing)` to unset an optimize hook.

## Examples

```julia
model = Model()
function my_hook(model::Model; kwargs...)
    print(kwargs)
    return optimize!(model; ignore_optimize_hook = true)
end
set_optimize_hook(model, my_hook)
optimize!(model; test_arg = true)
```
