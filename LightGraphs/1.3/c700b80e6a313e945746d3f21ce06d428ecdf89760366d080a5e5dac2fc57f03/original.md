```
diameter(eccentricities)
diameter(g, distmx=weights(g))
```

Given a graph and optional distance matrix, or a vector of precomputed eccentricities, return the maximum eccentricity of the graph.

# Examples

```jldoctest
julia> using LightGraphs

julia> diameter(star_graph(5))
2

julia> diameter(path_graph(5))
4
```
