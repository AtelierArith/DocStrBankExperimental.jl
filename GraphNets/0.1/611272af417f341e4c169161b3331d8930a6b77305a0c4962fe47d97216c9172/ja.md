```
batch(t::NamedTuple)
```

## 例:

```julia
dims = (DE, DN, DG) = 3, 4, 5
core = GNCore(dims)
adj_mat_1 = [
    1 0 1;
    1 1 0;
    0 0 1;
] # 隣接行列 1
num_nodes_1 = size(adj_mat_1, 1)
num_edges_1 = length(filter(isone, adj_mat_1))
adj_mat_2 = [
    1 0 1 0;
    1 1 0 1;
    0 0 1 0;
    1 1 0 1;
] # 隣接行列 2
num_nodes_2 = size(adj_mat_2, 1)
num_edges_2 = length(filter(isone, adj_mat_2))
edge_features = [
    rand(Float32, DE, num_edges_1),
    rand(Float32, DE, num_edges_2),
]
node_features = [
    rand(Float32, DN, num_nodes_1),
    rand(Float32, DN, num_nodes_2),
]
graph_features = [
    rand(Float32, DG),
    rand(Float32, DG),
]
adj_mats = [adj_mat_1,adj_mat_2]
batch_size = length(adj_mats)
x = (
    graphs=adj_mats,  # このバッチのグラフは異なる構造を持つ
    ef=edge_features, 
    nf=node_features,
    gf=graph_features
)
x_batched = batch(x)
edge_block_size = x_batched.graphs.edge_block_size
node_block_size = x_batched.graphs.node_block_size
@assert typeof(x_batched.graphs) == GraphNets.GNGraphBatch
@assert size(x_batched.ef) == (DE, edge_block_size, batch_size)
@assert size(x_batched.nf) == (DN, node_block_size, batch_size)
@assert size(x_batched.gf) == (DG, 1, batch_size)
```
