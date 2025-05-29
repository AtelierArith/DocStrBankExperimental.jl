```
articulation(g)
```

Compute the [articulation points](https://en.wikipedia.org/wiki/Biconnected_component) of a connected graph `g` and return an array containing all cut vertices.

# Examples

```jldoctest
julia> using Graphs

julia> articulation(star_graph(5))
1-element Vector{Int64}:
 1

julia> articulation(path_graph(5))
3-element Vector{Int64}:
 2
 3
 4
```
