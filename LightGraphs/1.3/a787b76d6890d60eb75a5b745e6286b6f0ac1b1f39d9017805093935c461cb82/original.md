```
tensor_product(g, h)
```

Return the [tensor product](https://en.wikipedia.org/wiki/Tensor_product_of_graphs) of `g` and `h`.

### Implementation Notes

Preserves the eltype of the input graph. Will error if the number of vertices in the generated graph exceeds the eltype.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = tensor_product(star_graph(3), path_graph(3))
{9, 8} undirected simple Int64 graph

julia> collect(edges(g))
8-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 5
 Edge 1 => 8
 Edge 2 => 4
 Edge 2 => 6
 Edge 2 => 7
 Edge 2 => 9
 Edge 3 => 5
 Edge 3 => 8
```
