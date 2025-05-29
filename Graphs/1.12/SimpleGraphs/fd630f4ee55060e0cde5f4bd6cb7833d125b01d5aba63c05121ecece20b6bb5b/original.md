```
SimpleDiGraph{T}(g::SimpleDiGraph)
```

Construct a copy of g. If the element type `T` is specified, the vertices of `g` are converted to this type. Otherwise the element type is the same as for `g`.

## Examples

```jldoctest
julia> using Graphs

julia> g = complete_digraph(5)
{5, 20} directed simple Int64 graph

julia> SimpleDiGraph{UInt8}(g)
{5, 20} directed simple UInt8 graph
```
