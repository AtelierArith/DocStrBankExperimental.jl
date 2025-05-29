```
vertices(g)
```

Return (an iterator to or collection of) the vertices of a graph.

### Implementation Notes

A returned iterator is valid for one pass over the edges, and is invalidated by changes to `g`.

# Examples

```jldoctest
julia> using Graphs

julia> collect(vertices(SimpleGraph(4)))
4-element Vector{Int64}:
 1
 2
 3
 4
```
