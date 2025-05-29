```
JuMP.optimize!(model::InfiniteModel; [kwargs...])
```

Extend `JuMP.optimize!` to optimize infinite models using the internal optimizer model. Will call [`build_optimizer_model!`](@ref) if the optimizer model isn't up to date. The `kwargs` correspond to keyword arguments passed to [`build_optimizer_model!`](@ref) if any are defined.

**Example**

```julia-repl
julia> optimize!(model)

julia> has_values(model)
true
```
