```
cartesian_product(g, h)
```

Return the [cartesian product](https://en.wikipedia.org/wiki/Cartesian_product_of_graphs) of `g` and `h`.

### Implementation Notes

Preserves the eltype of the input graph. Will error if the number of vertices in the generated graph exceeds the eltype.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = cartesian_product(star_graph(3), path_graph(3))
{9, 12} undirected simple Int64 graph

julia> collect(edges(g))
12-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 1 => 4
 Edge 1 => 7
 Edge 2 => 3
 Edge 2 => 5
 Edge 2 => 8
 Edge 3 => 6
 Edge 3 => 9
 Edge 4 => 5
 Edge 5 => 6
 Edge 7 => 8
 Edge 8 => 9
```
