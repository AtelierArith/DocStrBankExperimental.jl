```
biconnected_components(g) -> Vector{Vector{Edge{eltype(g)}}}
```

Compute the [biconnected components](https://en.wikipedia.org/wiki/Biconnected_component) of an undirected graph `g`and return a vector of vectors containing each biconnected component.

Performance: Time complexity is $\mathcal{O}(|V|)$.

# Examples

```jldoctest
julia> using LightGraphs

julia> biconnected_components(star_graph(5))
4-element Array{Array{LightGraphs.SimpleGraphs.SimpleEdge,1},1}:
 [Edge 1 => 3]
 [Edge 1 => 4]
 [Edge 1 => 5]
 [Edge 1 => 2]

julia> biconnected_components(cycle_graph(5))
1-element Array{Array{LightGraphs.SimpleGraphs.SimpleEdge,1},1}:
 [Edge 1 => 5, Edge 4 => 5, Edge 3 => 4, Edge 2 => 3, Edge 1 => 2]
```
