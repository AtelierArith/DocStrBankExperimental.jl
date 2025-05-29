```
add_vertex!(g)
```

Add a new vertex to the graph `g`. Return `true` if addition was successful.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(Int8(typemax(Int8) - 1))
{126, 0} undirected simple Int8 graph

julia> add_vertex!(g)
true

julia> add_vertex!(g)
false
```
