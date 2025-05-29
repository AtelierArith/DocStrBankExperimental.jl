```
ShiftNet
```

Shifts mapped to tree nodes and their (unique) parent edge on a [`PhyloNetworks.HybridNetwork`](@extref) sorted in topological order. Its `shift` field is a vector of shift values, one for each node, corresponding to the shift on the parent edge of the node (which makes sense for tree nodes only: they have a single parent edge).

Two `ShiftNet` objects on the same network can be concatened with `*`.

`ShiftNet(node::Vector{Node}, value::AbstractVector, net::HybridNetwork; checkpreorder::Bool=true)`

Constructor from a vector of nodes and associated values. The shifts are located on the edges above the nodes provided. Warning, shifts on hybrid edges are not allowed.

`ShiftNet(edge::Vector{Edge}, value::AbstractVector, net::HybridNetwork; checkpreorder::Bool=true)`

Constructor from a vector of edges and associated values. Warning, shifts on hybrid edges are not allowed.

Extractors: [`getshiftedgenumber`](@ref), [`getshiftvalue`](@ref)
