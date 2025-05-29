```
map_agent_groups(order::Int, f::Function, model::ABM; kwargs...)
map_agent_groups(order::Int, f::Function, model::ABM, filter::Function; kwargs...)
```

Applies function `f` to all grouped agents of an [`iter_agent_groups`](@ref) iterator. `kwargs` are passed to the iterator method. `f` must take the form `f(NTuple{O,AgentType})`, where the dimension `O` is equal to `order`.

Optionally, a `filter` function that accepts an iterable and returns a `Bool` can be applied to remove unwanted matches from the results. **Note:** This option cannot keep matrix order, so should be used in conjunction with [`index_mapped_groups`](@ref) to associate agent ids with the resultant data.
