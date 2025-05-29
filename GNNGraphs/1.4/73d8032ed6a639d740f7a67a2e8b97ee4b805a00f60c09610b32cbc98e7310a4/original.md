```
NeighborLoader(graph; num_neighbors, input_nodes, num_layers, [batch_size])
```

A data structure for sampling neighbors from a graph for training Graph Neural Networks (GNNs).  It supports multi-layer sampling of neighbors for a batch of input nodes, useful for mini-batch training originally introduced in ["Inductive Representation Learning on Large Graphs"}(https://arxiv.org/abs/1706.02216) paper.

# Fields

  * `graph::GNNGraph`: The input graph.
  * `num_neighbors::Vector{Int}`: A vector specifying the number of neighbors to sample per node at each GNN layer.
  * `input_nodes::Vector{Int}`: A vector containing the starting nodes for neighbor sampling.
  * `num_layers::Int`: The number of layers for neighborhood expansion (how far to sample neighbors).
  * `batch_size::Union{Int, Nothing}`: The size of the batch. If not specified, it defaults to the number of `input_nodes`.

# Examples

```julia
julia> loader = NeighborLoader(graph; num_neighbors=[10, 5], input_nodes=[1, 2, 3], num_layers=2)

julia> batch_counter = 0

julia> for mini_batch_gnn in loader
            batch_counter += 1
            println("Batch ", batch_counter, ": Nodes in mini-batch graph: ", nv(mini_batch_gnn))
        end
```
