```
add_prm_edges!(prm,src_node_num,max_num_edges,is_edge_valid,edge_cost)
```

この関数は、prm（グラフ）の特定のノードにエッジを追加します。

# 引数

  * `prm::MetaGraph` -> 新しいエッジが追加されるグラフ
  * `src_node_num::Int` -> 新しいエッジが追加されるprm（グラフ）のノード番号
  * `max_num_edges::Int` -> このノードがprm（グラフ）で持つことができる最大エッジ数
  * `is_edge_valid::Function` -> 与えられたエッジがグラフに追加するのに有効かどうかをチェックする関数。入力としてprm（グラフ）、ソースノードの状態、宛先ノードの状態を受け取り、真または偽を返します（この関数は、ソースノードの状態を持つノードと宛先ノードの状態を持つノードを接続するエッジが環境内の障害物を通過するかどうかをチェックするために使用できます）。

```julia-repl
    is_edge_valid(prm,src_node_state,des_node_state)
```

  * `edge_cost::Function` -> グラフの2つのノード間のエッジのコストを計算する関数。入力としてprm（グラフ）、ソースノードの状態、宛先ノードの状態を受け取り、これらのノードを接続するエッジのコストを返します（ノードの状態が（x,y）位置である2D環境の場合、この関数は2つのノード間のユークリッド距離を返すことができます）。次のように呼び出されます：`edge_cost(prm,src_node_state,des_node_state)`

```julia-repl
    edge_cost(prm,src_node_state,des_node_state)
```

# 例

```julia-repl
add_prm_edges!(prm, 11, 5, is_edge_valid, edge_cost)
```
