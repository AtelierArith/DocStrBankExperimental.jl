```
SimpleGraphFromIterator(iter)
```

Create a [`SimpleGraph`](@ref) from an iterator `iter`. The elements in iter must be of `type <: SimpleEdge`.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 3);

julia> h = SimpleGraphFromIterator(edges(g));

julia> collect(edges(h))
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3
```
