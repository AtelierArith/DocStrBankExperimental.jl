```
set_optimize_hook(model::GenericModel, f::Union{Function,Nothing})
```

Set the function `f` as the optimize hook for `model`.

`f` should have a signature `f(model::GenericModel; kwargs...)`, where the `kwargs` are those passed to [`optimize!`](@ref).

## Notes

  * The optimize hook should generally modify the model, or some external state in some way, and then call `optimize!(model; ignore_optimize_hook = true)` to optimize the problem, bypassing the hook.
  * Use `set_optimize_hook(model, nothing)` to unset an optimize hook.

## Example

```jldoctest
julia> model = Model();

julia> function my_hook(model::Model; kwargs...)
           println(kwargs)
           println("Calling with `ignore_optimize_hook = true`")
           optimize!(model; ignore_optimize_hook = true)
           return
       end
my_hook (generic function with 1 method)

julia> set_optimize_hook(model, my_hook)
my_hook (generic function with 1 method)

julia> optimize!(model; test_arg = true)
Base.Pairs{Symbol, Bool, Tuple{Symbol}, @NamedTuple{test_arg::Bool}}(:test_arg => 1)
Calling with `ignore_optimize_hook = true`
ERROR: NoOptimizer()
[...]
```
