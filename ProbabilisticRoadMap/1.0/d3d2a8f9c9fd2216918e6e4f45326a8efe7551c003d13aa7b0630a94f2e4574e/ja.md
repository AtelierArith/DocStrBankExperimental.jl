```
generate_prm(num_nodes,max_edges,get_node_values,is_node_valid,is_edge_valid,edge_cost,rng,time_limit=0.2)
```

この関数は、指定された数のノードを持つ prm（グラフ）を生成し、他のノードに接続します。

# 引数

  * `num_nodes::Int` -> prm（グラフ）に追加されるノードの数
  * `max_edges::Int` -> prm（グラフ）内の各ノードが持つことができる最大エッジ数
  * `get_node_state::Function` -> そのノードに保存される状態を返す関数。ランダム数生成器を入力として受け取り、ノードの状態を返します（2D環境の場合、ノードの状態はxおよびy位置のタプルである可能性があります）。

```julia-repl
    node_state = get_node_state(rng)
```

  * `is_node_valid::Function` -> 指定されたノードがPRMに追加するのに有効かどうかをチェックする関数。prm（グラフ）とノードの状態を入力として受け取り、真または偽を返します（この関数は、ノードの状態が自由空間にあるかどうかをチェックするために使用できます）。

```julia-repl
    is_node_valid(prm,node_state)

```

  * `is_edge_valid::Function` -> 指定されたエッジがグラフに追加するのに有効かどうかをチェックする関数。prm（グラフ）、ソースノードの状態、および宛先ノードの状態を入力として受け取り、真または偽を返します（この関数は、ソースノードの状態を持つノードと宛先ノードの状態を持つノードを接続するエッジが環境内の障害物を通過するかどうかをチェックするために使用できます）。

```julia-repl
    is_edge_valid(prm,src_node_state,des_node_state)
```

  * `edge_cost::Function` -> グラフの2つのノード間のエッジのコストを計算する関数。prm（グラフ）、ソースノードの状態、および宛先ノードの状態を入力として受け取り、これらのノードを接続するエッジのコストを返します（ノードの状態が（x,y）位置である2D環境の場合、この関数は2つのノード間のユークリッド距離を返すことができます）。

```julia-repl
    edge_cost(prm,src_node_state,des_node_state)
```

  * `rng::AbstractRNG` -> ランダム数生成器オブジェクト。PRM内の新しいノードの状態を生成するために`get_node_state`関数への入力として使用されます。
  * `time_limit::Real=0.2` -> prm（グラフ）に新しいノードを追加するための時間制限を指定します。

# 出力

  * `num_nodes`個の頂点（ノード）を持つメタグラフで、各頂点は`max_edges`個以下の他の頂点に接続されています。

    ```
      （すべてのノードに`:values`という属性があり、その中にノードの値が含まれているためメタグラフです）
    ```

# 例

```julia-repl
generate_prm(100,5,get_node_values,is_node_valid,is_edge_valid,edge_cost,MersenneTwister(11),1.0)
```
