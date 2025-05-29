```
TAGConv(in => out, k=3; bias=true, init=glorot_uniform, add_self_loops=true, use_edge_weight=false)
```

TAGConv layer from [Topology Adaptive Graph Convolutional Networks](https://arxiv.org/pdf/1710.10370.pdf). This layer extends the idea of graph convolutions by applying filters that adapt to the topology of the data.  It performs the operation:

$$
H^{K} = {\sum}_{k=0}^K (D^{-1/2} A D^{-1/2})^{k} X {\Theta}_{k}
$$

where `A` is the adjacency matrix of the graph, `D` is the degree matrix, `X` is the input feature matrix, and ${\Theta}_{k}$ is a unique weight matrix for each hop `k`.

# Arguments

  * `in`: Number of input features.
  * `out`: Number of output features.
  * `k`: Maximum number of hops to consider. Default is `3`.
  * `bias`: Whether to include a learnable bias term. Default is `true`.
  * `init`: Initialization function for the weights. Default is `glorot_uniform`.
  * `add_self_loops`: Whether to add self-loops to the adjacency matrix. Default is `true`.
  * `use_edge_weight`: If `true`, edge weights are considered in the computation (if available). Default is `false`.

# Examples

```julia
# Example graph data
s = [1, 1, 2, 3]
t = [2, 3, 1, 1]
g = GNNGraph(s, t)  # Create a graph
x = randn(Float32, 3, g.num_nodes)  # Random features for each node

# Create a TAGConv layer
l = TAGConv(3 => 5, k=3; add_self_loops=true)

# Apply the TAGConv layer
y = l(g, x)  # Output size: 5 × num_nodes
```
