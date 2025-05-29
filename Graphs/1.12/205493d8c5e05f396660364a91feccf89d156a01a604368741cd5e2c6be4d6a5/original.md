```
edges(g)
```

Return (an iterator to or collection of) the edges of a graph. For `AbstractSimpleGraph`s it returns a `SimpleEdgeIter` (lexicographical order). The expressions `e in edges(g)` and `e ∈ edges(g)` evaluate as calls to [`has_edge`](@ref).

### Implementation Notes

A returned iterator is valid for one pass over the edges, and is invalidated by changes to `g`.

# Examples

```jldoctest
julia> using Graphs

julia> g = path_graph(3);

julia> collect(edges(g))
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3
```
