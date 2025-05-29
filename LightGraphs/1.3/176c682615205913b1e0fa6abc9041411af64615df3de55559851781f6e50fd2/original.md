```
join(g, h)
```

Return a graph that combines graphs `g` and `h` using `blockdiag` and then adds all the edges between the vertices in `g` and those in `h`.

### Implementation Notes

Preserves the eltype of the input graph. Will error if the number of vertices in the generated graph exceeds the eltype.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = join(star_graph(3), path_graph(2))
{5, 9} undirected simple Int64 graph

julia> collect(edges(g))
9-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 1 => 5
 Edge 2 => 4
 Edge 2 => 5
 Edge 3 => 4
 Edge 3 => 5
 Edge 4 => 5
```
