```
articulation(g)
```

Compute the [articulation points](https://en.wikipedia.org/wiki/Biconnected_component) of a connected graph `g` and return an array containing all cut vertices.

# Examples

```jldoctest
julia> using LightGraphs

julia> articulation(star_graph(5))
1-element Array{Int64,1}:
 1

julia> articulation(path_graph(5))
3-element Array{Int64,1}:
 2
 3
 4
```
