```
SimpleDiGraph(g::AbstractSimpleGraph)
```

Construct an directed `SimpleDiGraph` from a graph `g`. The element type is the same as for `g`.

## Examples

```jldoctest
julia> using Graphs

julia> g = path_graph(Int8(5))
{5, 4} undirected simple Int8 graph

julia> SimpleDiGraph(g)
{5, 8} directed simple Int8 graph
```
