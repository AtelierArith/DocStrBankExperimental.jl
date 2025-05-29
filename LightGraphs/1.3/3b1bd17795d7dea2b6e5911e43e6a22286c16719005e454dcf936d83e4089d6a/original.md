```
maximal_cliques(g)
```

Return a vector of vectors representing the node indices in each of the maximal cliques found in the undirected graph `g`.

```jldoctest
julia> using LightGraphs
julia> g = SimpleGraph(3)
julia> add_edge!(g, 1, 2)
julia> add_edge!(g, 2, 3)
julia> maximal_cliques(g)
2-element Array{Array{Int64,N},1}:
 [2,3]
 [2,1]
```
