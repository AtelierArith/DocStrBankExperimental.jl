```
GNCore(dims; dropout=0)
```

Initializes an instance of the **`GNCore`** type, representing a GraphNet "core" block.

The following keyword arguments are supported:

  * `dropout` (Defaults to 0)

## Example:

```julia
dims = (DE, DN, DG) = 3, 4, 5
core = GNCore(dims)
adj_mat = adj_mat = [
    1 0 1;
    1 1 0;
    0 0 1;
]
num_nodes = size(adj_mat, 1)
num_edges = length(filter(isone, adj_mat))
batch_size = 2
edge_features = rand(Float32, DE, num_edges, batch_size)
node_features = rand(Float32, DN, num_nodes, batch_size)
graph_features = rand(Float32, DG, batch_size)
x = (
    graphs=adj_mat, # All graphs in this batch have same structure
    ef=edge_features, # (DE, num_edges, batch_size)
    nf=node_features, # (DN, num_nodes, batch_size)
    gf=graph_features # no input graph features
) |> batch
y = core(x) |> unbatch
@assert size(y.ef) == (DE, num_edges, batch_size)
@assert size(y.nf) == (DN, num_nodes, batch_size)
@assert size(y.gf) == (DG, batch_size)
```
