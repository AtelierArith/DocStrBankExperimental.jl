```
center(eccentricities)
center(g, distmx=weights(g))
```

Given a graph and optional distance matrix, or a vector of precomputed eccentricities, return the set of all vertices whose eccentricity is equal to the graph's radius (that is, the set of vertices with the smallest eccentricity).

# Examples

```jldoctest
julia> using Graphs

julia> center(star_graph(5))
1-element Vector{Int64}:
 1

julia> center(path_graph(5))
1-element Vector{Int64}:
 3
```
