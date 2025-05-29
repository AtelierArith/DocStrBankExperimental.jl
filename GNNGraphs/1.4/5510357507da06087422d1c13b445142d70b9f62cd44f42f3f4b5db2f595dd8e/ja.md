```
sample_neighbors(g, nodes, K=-1; dir=:in, replace=false, dropnodes=false)
```

指定されたノードの隣接エッジをサンプリングし、誘導サブグラフを返します。各ノードについて、いくつかのインバウンド（または`dir = :out`の場合はアウトバウンド）エッジがランダムに選択されます。`dropnodes=false`の場合、返されるグラフには元のグラフのすべてのノードが含まれますが、サンプリングされたエッジのみが含まれます。

返されるグラフには、元のグラフのエッジのIDに対応するエッジ特徴`EID`が含まれます。`dropnodes=true`の場合、元のグラフのノードIDを持つノード特徴`NID`も含まれます。

# 引数

  * `g`. グラフ。
  * `nodes`. 隣接ノードをサンプリングするためのノードIDのリスト。
  * `K`. 各ノードに対してサンプリングされる最大エッジ数。-1の場合、すべての隣接エッジが選択されます。
  * `dir`. インバウンド（`:in`）またはアウトバウンド（$:out$）エッジをサンプリングするかどうかを決定します（デフォルトは`:in`）。
  * `replace`. `true`の場合、置換ありでサンプリングします。
  * `dropnodes`. `true`の場合、結果のサブグラフにはサンプリングされたエッジに関与するノードのみが含まれます。

# 例

```julia
julia> g = rand_graph(20, 100)
GNNGraph:
    num_nodes = 20
    num_edges = 100

julia> sample_neighbors(g, 2:3)
GNNGraph:
    num_nodes = 20
    num_edges = 9
    edata:
        EID => (9,)

julia> sg = sample_neighbors(g, 2:3, dropnodes=true)
GNNGraph:
    num_nodes = 10
    num_edges = 9
    ndata:
        NID => (10,)
    edata:
        EID => (9,)

julia> sg.ndata.NID
10-element Vector{Int64}:
  2
  3
 17
 14
 18
 15
 16
 20
  7
 10

julia> sample_neighbors(g, 2:3, 5, replace=true)
GNNGraph:
    num_nodes = 20
    num_edges = 10
    edata:
        EID => (10,)
```
