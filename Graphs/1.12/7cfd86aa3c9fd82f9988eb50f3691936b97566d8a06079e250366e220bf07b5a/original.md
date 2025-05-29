```
is_bipartite(g)
```

Return `true` if graph `g` is [bipartite](https://en.wikipedia.org/wiki/Bipartite_graph).

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 3);

julia> is_bipartite(g)
true

julia> add_edge!(g, 1, 3);

julia> is_bipartite(g)
false
```
