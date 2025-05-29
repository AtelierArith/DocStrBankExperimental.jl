```
SimpleDiGraph{T}(n=0)
```

Construct a `SimpleDiGraph{T}` with `n` vertices and 0 edges. If not specified, the element type `T` is the type of `n`.

## Examples

```jldoctest
julia> using Graphs

julia> SimpleDiGraph(UInt8(10))
{10, 0} directed simple UInt8 graph
```
