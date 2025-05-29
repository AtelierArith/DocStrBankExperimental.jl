```
local_clustering_coefficient(g, v)
local_clustering_coefficient(g, vs)
```

Return the [local clustering coefficient](https://en.wikipedia.org/wiki/Clustering_coefficient) for node `v` in graph `g`. If a list of vertices `vs` is specified, return a vector of coefficients for each node in the list.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(4);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 4);

julia> add_edge!(g, 4, 1);

julia> local_clustering_coefficient(g, [1, 2, 3])
3-element Vector{Float64}:
 1.0
 1.0
 0.0
```
