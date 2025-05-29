```
periphery(eccentricities)
periphery(g, distmx=weights(g))
```

Given a graph and optional distance matrix, or a vector of precomputed eccentricities, return the set of all vertices whose eccentricity is equal to the graph's diameter (that is, the set of vertices with the largest eccentricity).

# Examples

```jldoctest
julia> using LightGraphs

julia> periphery(star_graph(5))
4-element Array{Int64,1}:
 2
 3
 4
 5

julia> periphery(path_graph(5))
2-element Array{Int64,1}:
 1
 5
```
