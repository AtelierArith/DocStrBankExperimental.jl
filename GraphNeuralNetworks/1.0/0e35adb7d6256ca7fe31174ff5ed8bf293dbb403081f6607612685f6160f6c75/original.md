```
HeteroGraphConv(itr; aggr = +)
HeteroGraphConv(pairs...; aggr = +)
```

A convolutional layer for heterogeneous graphs.

The `itr` argument is an iterator of `pairs` of the form `edge_t => layer`, where `edge_t` is a 3-tuple of the form `(src_node_type, edge_type, dst_node_type)`, and `layer` is a  convolutional layers for homogeneous graphs. 

Each convolution is applied to the corresponding relation.  Since a node type can be involved in multiple relations, the single convolution outputs  have to be aggregated using the `aggr` function. The default is to sum the outputs.

# Forward Arguments

  * `g::GNNHeteroGraph`: The input graph.
  * `x::Union{NamedTuple,Dict}`: The input node features. The keys are node types and the values are node feature tensors.

# Examples

```jldoctest
julia> g = rand_bipartite_heterograph((10, 15), 20)
GNNHeteroGraph:
  num_nodes: Dict(:A => 10, :B => 15)
  num_edges: Dict((:A, :to, :B) => 20, (:B, :to, :A) => 20)

julia> x = (A = rand(Float32, 64, 10), B = rand(Float32, 64, 15));

julia> layer = HeteroGraphConv((:A, :to, :B) => GraphConv(64 => 32, relu),
                               (:B, :to, :A) => GraphConv(64 => 32, relu));

julia> y = layer(g, x); # output is a named tuple

julia> size(y.A) == (32, 10) && size(y.B) == (32, 15)
true
```
