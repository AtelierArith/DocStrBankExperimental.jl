```julia
struct NestedEdge{T<:Integer} <: Graphs.SimpleGraphs.AbstractSimpleEdge{T<:Integer}
```

  * `src::Tuple{T, T} where T<:Integer`
  * `dst::Tuple{T, T} where T<:Integer`

A `NestedEdge` connects graphs inside a `NestedGraph` or simply nodes inside a `NestedGraph`. The `NestedEdge` connects two `NestedVertex`s. This means that every `NestedEdge` connects to a specific node and not as a hyperedge to the whole subgraph graph.
