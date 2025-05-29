```
radius(eccentricities)
radius(g, distmx=weights(g))
```

Given a graph and optional distance matrix, or a vector of precomputed eccentricities, return the minimum eccentricity of the graph.

# Examples

```jldoctest
julia> using LightGraphs

julia> radius(star_graph(5))
1

julia> radius(path_graph(5))
2
```
