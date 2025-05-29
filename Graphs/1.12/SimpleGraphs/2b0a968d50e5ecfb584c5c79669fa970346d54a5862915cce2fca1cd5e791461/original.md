```
SimpleGraph{T}(nv, ne; rng=nothing, seed=nothing)
```

Construct a random `SimpleGraph{T}` with `nv` vertices and `ne` edges. The graph is sampled uniformly from all such graphs. If `seed >= 0`, a random generator is seeded with this value. If not specified, the element type `T` is the type of `nv`.

### See also

[`erdos_renyi`](@ref)

## Examples

```jldoctest
julia> using Graphs

julia> SimpleGraph(5, 7)
{5, 7} undirected simple Int64 graph
```
