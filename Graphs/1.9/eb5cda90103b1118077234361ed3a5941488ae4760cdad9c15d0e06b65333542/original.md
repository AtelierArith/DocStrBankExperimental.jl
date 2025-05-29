```
is_directed(G)
```

Return `true` if the graph type `G` is a directed graph; `false` otherwise. New graph types must implement `is_directed(::Type{<:G})`. The method can also be called with `is_directed(g::G)`

# Examples

```jldoctest
julia> using Graphs

julia> is_directed(SimpleGraph(2))
false

julia> is_directed(SimpleGraph)
false

julia> is_directed(SimpleDiGraph(2))
true
```
