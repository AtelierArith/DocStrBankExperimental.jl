```
has_edge(g, s, d)
```

Return true if the graph `g` has an edge from node `s` to node `d`.

An optional `has_edge(g, e)` can be implemented to check if an edge belongs to a graph, including any data other than source and destination node.

`e in edges(g)` or `e ∈ edges(g)` evaluate as calls to `has_edge`, c.f. [`edges`](@ref).

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph(2);

julia> add_edge!(g, 1, 2);

julia> has_edge(g, 1, 2)
true

julia> has_edge(g, 2, 1)
false
```
