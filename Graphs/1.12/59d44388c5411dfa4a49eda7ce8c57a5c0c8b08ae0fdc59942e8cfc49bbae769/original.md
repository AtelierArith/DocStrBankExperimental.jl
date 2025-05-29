```
maximal_cliques(g)
```

Return a vector of vectors representing the node indices in each of the maximal cliques found in the undirected graph `g`.

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3)
{3, 0} undirected simple Int64 graph

julia> add_edge!(g, 1, 2)
true

julia> add_edge!(g, 2, 3)
true

julia> maximal_cliques(g)
2-element Vector{Vector{Int64}}:
 [2, 3]
 [2, 1]
```
