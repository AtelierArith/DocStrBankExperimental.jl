```
NeighborLoader(graph; num_neighbors, input_nodes, num_layers, [batch_size])
```

グラフから隣接ノードをサンプリングするためのデータ構造で、グラフニューラルネットワーク（GNN）のトレーニングに使用されます。これは、ミニバッチトレーニングに便利な、入力ノードのバッチに対する隣接ノードの多層サンプリングをサポートします。これは、["Inductive Representation Learning on Large Graphs"](https://arxiv.org/abs/1706.02216) 論文で最初に導入されました。

# フィールド

  * `graph::GNNGraph`: 入力グラフ。
  * `num_neighbors::Vector{Int}`: 各GNN層でノードごとにサンプリングする隣接ノードの数を指定するベクター。
  * `input_nodes::Vector{Int}`: 隣接ノードサンプリングのための開始ノードを含むベクター。
  * `num_layers::Int`: 隣接ノード拡張の層数（どれだけ遠くまで隣接ノードをサンプリングするか）。
  * `batch_size::Union{Int, Nothing}`: バッチのサイズ。指定されていない場合、`input_nodes`の数にデフォルト設定されます。

# 例

```julia
julia> loader = NeighborLoader(graph; num_neighbors=[10, 5], input_nodes=[1, 2, 3], num_layers=2)

julia> batch_counter = 0

julia> for mini_batch_gnn in loader
            batch_counter += 1
            println("バッチ ", batch_counter, ": ミニバッチグラフのノード数: ", nv(mini_batch_gnn))
        end
```
