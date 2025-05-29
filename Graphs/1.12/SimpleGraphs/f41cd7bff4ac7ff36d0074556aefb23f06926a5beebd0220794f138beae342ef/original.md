```
SimpleGraph{T}(n=0)
```

Construct a `SimpleGraph{T}` with `n` vertices and 0 edges. If not specified, the element type `T` is the type of `n`.

## Examples

```jldoctest
julia> using Graphs

julia> SimpleGraph(UInt8(10))
{10, 0} undirected simple UInt8 graph
```
