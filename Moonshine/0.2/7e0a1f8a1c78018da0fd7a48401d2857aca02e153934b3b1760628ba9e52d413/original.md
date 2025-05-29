```julia
next_inconsistent_idx(
    arg,
    idx,
    stack;
    mutations_edges,
    buffer
)

```

Index of the next inconsistent marker, that is the next which mutates more than once in a given ancestral recombination graph.

`stack` must be of type `CheapStack{Edge{VertexType}}` (see [`CheapStack`](@ref)).
