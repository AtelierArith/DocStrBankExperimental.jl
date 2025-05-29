```
GNBlock(in => out;  dropout=0)
```

**`GNBlock`** 型のインスタンスを初期化し、GraphNet ブロックを表します。

次のキーワード引数がサポートされています：

  * `dropout`（デフォルトは 0）

## 例：

```julia
in_dims = (X_DE, X_DN, X_DG) = 10, 5, 0
out_dims = (Y_DE, Y_DN, Y_DG) = 3, 4, 5
block = GNBlock(in_dims => out_dims)
adj_mat = adj_mat = [
    1 0 1;
    1 1 0;
    0 0 1;
]
num_nodes = size(adj_mat, 1)
num_edges = length(filter(isone, adj_mat))
batch_size = 2
edge_features = rand(Float32, X_DE, num_edges, batch_size)
node_features = rand(Float32, X_DN, num_nodes, batch_size)
graph_features = nothing # グラフレベルの入力特徴はなし
x = (
    graphs=adj_mat, # このバッチ内のすべてのグラフは同じ構造を持つ
    ef=edge_features, # (X_DE, num_edges, batch_size)
    nf=node_features, # (X_DN, num_nodes, batch_size)
    gf=graph_features # 入力グラフ特徴はなし
) |> batch
y = block(x) |> unbatch
@assert size(y.ef) == (Y_DE, num_edges, batch_size)
@assert size(y.nf) == (Y_DN, num_nodes, batch_size)
@assert size(y.gf) == (Y_DG, batch_size)
```
