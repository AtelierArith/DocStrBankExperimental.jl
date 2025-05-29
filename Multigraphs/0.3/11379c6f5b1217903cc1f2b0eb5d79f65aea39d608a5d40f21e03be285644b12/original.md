```
MultipleEdge{T, U} <: AbstractMultipleEdge{T, U}
```

A struct representing multiple edges.

## Examples

```jltestdoc
julia> using Graphs, Multigraphs

julia> me = MultipleEdge(1, 2, 3)
Multiple edge 1 => 2 with multiplicity 3

julia> for e in me println(e) end
Edge 1 => 2
Edge 1 => 2
Edge 1 => 2

```
