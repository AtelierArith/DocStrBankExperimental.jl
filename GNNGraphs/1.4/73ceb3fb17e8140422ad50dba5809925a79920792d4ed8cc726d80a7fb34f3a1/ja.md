```
perturb_edges([rng], g::GNNGraph, perturb_ratio)
```

指定された `perturb_ratio` に基づいて、ランダムなエッジを追加することによって `g` から得られる新しいグラフを返します。 `perturb_ratio` は、グラフ内の現在のエッジの数に対する新しいエッジの追加割合を決定します。これらの新しいエッジは、自己ループを作成することなく追加されます。

この関数は、いくつかの基礎データを `g` と共有しながら、追加のエッジを含む新しい `GNNGraph` インスタンスを返します。新しいエッジのノードはランダムに選択され、これらの新しいエッジにはエッジデータ（`edata`）や重み（`w`）は割り当てられません。

# 引数

  * `g::GNNGraph`: 変化させるグラフ。
  * `perturb_ratio`: グラフ内の現在のエッジの数に対する新しいエッジの追加割合。例えば、`perturb_ratio` が 0.1 の場合、現在のエッジの数の 10% が新しいランダムエッジとして追加されます。
  * `rng`: 再現可能な結果を保証するためのオプションの乱数生成器。

# 例

```julia
julia> g = GNNGraph((s, t, w))
GNNGraph:
  num_nodes: 4
  num_edges: 5

julia> perturbed_g = perturb_edges(g, 0.2)
GNNGraph:
  num_nodes: 4
  num_edges: 6
```
