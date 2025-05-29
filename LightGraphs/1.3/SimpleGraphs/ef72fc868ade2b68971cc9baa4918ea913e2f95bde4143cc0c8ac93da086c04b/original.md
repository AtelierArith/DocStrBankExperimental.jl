```
SimpleGraph(g::SimpleDiGraph)
```

Construct an undirected `SimpleGraph` from a directed `SimpleDiGraph`. Every directed edge in `g` is added as an undirected edge. The element type is the same as for `g`.

## Examples

```jldoctest
julia> g = path_digraph(Int8(5))
julia> SimpleGraph(g)
{5, 4} undirected simple Int8 graph
```
