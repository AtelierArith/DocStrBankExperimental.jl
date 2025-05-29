```
has_edge(sim, id::AgentID, ::Type{E})
```

Returns true if there is at least one edge of type `E` with agent `id` as target.

`has_edge` is not defined if T has the :SingleEdge and :SingleType hints, with the exception that it has also the :IgnoreFrom and :Stateless hints.

See also [`apply!`](@ref), [`edges`](@ref), [`neighborids`](@ref), [`edgestates`](@ref), [`num_edges`](@ref) and [`neighborstates`](@ref)
