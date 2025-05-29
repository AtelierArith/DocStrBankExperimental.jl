```
fill_space!([A ,] model::ABM{<:DiscreteSpace,A}, args...)
fill_space!([A ,] model::ABM{<:DiscreteSpace,A}; kwargs...)
fill_space!([A ,] model::ABM{<:DiscreteSpace,A}, f::Function)
```

Add one agent to each position in the model's space. Similarly with [`add_agent!`](@ref), `fill_space` creates the necessary agents and adds them to the model. Like in [`add_agent!`](@ref) you may use either `args...` or `kwargs...` to set the remaining properties of the agent.

Alternatively, you may use the third version. If instead of `args...` a function `f` is provided, then `args = f(pos)` is the result of applying `f` where `pos` is each position (tuple for grid, integer index for graph). Hence, in this case `f` must create all other agent properties besides mandatory `id, pos`.

An optional first argument is an agent **type** to be created, and targets mixed agent models where the agent constructor cannot be deduced (since it is a union).
