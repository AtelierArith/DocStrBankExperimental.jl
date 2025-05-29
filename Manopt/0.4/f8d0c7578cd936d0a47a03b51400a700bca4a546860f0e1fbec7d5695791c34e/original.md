```
get_state(s::AbstractManoptSolverState, recursive::Bool=true)
```

return the (one step) undecorated [`AbstractManoptSolverState`](@ref) of the (possibly) decorated `s`. As long as your decorated state stores the state within `s.state` and the [`dispatch_objective_decorator`](@ref) is set to `Val{true}`, the internal state are extracted automatically.

By default the state that is stored within a decorated state is assumed to be at `s.state`. Overwrite `_get_state(s, ::Val{true}, recursive) to change this behaviour for your state`s` for both the recursive and the direct case.

If `recursive` is set to `false`, only the most outer decorator is taken away instead of all.
