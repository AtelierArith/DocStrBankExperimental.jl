```
add_prm_node!(prm,get_node_state,is_node_valid,rng,time_limit)
```

この関数は、指定された時間制限内に与えられた prm（グラフ）に新しいノードを追加しようとします。

# 引数

  * `prm::MetaGraph` -> 新しいノード（頂点）を追加するグラフ
  * `get_node_state::Function` -> そのノードに保存される状態を返す関数。ランダム数生成器を入力として受け取り、ノードの状態を返します（2D環境の場合、ノードの状態は x および y の位置のタプルである可能性があります）。

```julia-repl
        node_state = get_node_state(rng)
```

  * `is_node_valid::Function` -> 与えられたノードが PRM に追加するのに有効かどうかをチェックする関数。prm（グラフ）とノードの状態を入力として受け取り、true または false を返します（この関数は、ノードの状態が自由空間にあるかどうかをチェックするために使用できます）。

```julia-repl
        is_node_valid(prm,node_state)
```

  * `rng::AbstractRNG` -> ランダム数生成器オブジェクト。PRM の新しいノードの状態を生成するために `get_node_state` 関数への入力として使用されます。
  * `time_limit::Real=0.2` -> prm（グラフ）に新しいノードを追加するための時間制限を指定します。

# 出力

  * prm（グラフ）に新しいノードが正常に追加された場合は `true`、そうでない場合は `false`

# 例

```julia-repl
add_prm_node!(prm,get_node_state,is_node_valid,MersenneTwister(11),1.0)
```
