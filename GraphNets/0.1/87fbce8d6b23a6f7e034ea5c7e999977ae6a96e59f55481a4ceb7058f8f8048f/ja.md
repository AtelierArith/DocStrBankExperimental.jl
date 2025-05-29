```
GNCore(dims; dropout=0)
```

**`GNCore`** 型のインスタンスを初期化し、GraphNetの「コア」ブロックを表します。

次のキーワード引数がサポートされています：

  * `dropout`（デフォルトは0）

## 例：

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
    graphs=adj_mat, # このバッチ内のすべてのグラフは同じ構造を持つ
    ef=edge_features, # (DE, num_edges, batch_size)
    nf=node_features, # (DN, num_nodes, batch_size)
    gf=graph_features # 入力グラフ特徴はなし
) |> batch
y = core(x) |> unbatch
@assert size(y.ef) == (DE, num_edges, batch_size)
@assert size(y.nf) == (DN, num_nodes, batch_size)
@assert size(y.gf) == (DG, batch_size)
```
