```
SimpleGraph{T}(g::SimpleGraph)
```

Construct a copy of g. If the element type `T` is specified, the vertices of `g` are converted to this type. Otherwise the element type is the same as for `g`.

## Examples

```jldoctest
julia> g = complete_graph(5)
julia> SimpleGraph{UInt8}(g)
{5, 10} undirected simple UInt8 graph
```
