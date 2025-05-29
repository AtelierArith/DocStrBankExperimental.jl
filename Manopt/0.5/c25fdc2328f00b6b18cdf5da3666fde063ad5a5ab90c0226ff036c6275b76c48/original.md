```
get_objective(o::AbstractManifoldObjective, recursive=true)
```

return the (one step) undecorated [`AbstractManifoldObjective`](@ref) of the (possibly) decorated `o`. As long as your decorated objective stores the objective within `o.objective` and the [`dispatch_objective_decorator`](@ref) is set to `Val{true}`, the internal state are extracted automatically.

By default the objective that is stored within a decorated objective is assumed to be at `o.objective`. Overwrite `_get_objective(o, ::Val{true}, recursive) to change this behaviour for your objective`o` for both the recursive and the direct case.

If `recursive` is set to `false`, only the most outer decorator is taken away instead of all.
