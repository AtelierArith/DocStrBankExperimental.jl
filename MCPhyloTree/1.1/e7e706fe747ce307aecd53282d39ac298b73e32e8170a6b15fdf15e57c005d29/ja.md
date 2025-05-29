```
randomize!(root::T, num::Int64=100)::Nothing where T <:AbstractNode
```

この関数は、最近接隣接交換（NNI）移動の数と枝の長さのランダム化を行うことによって木をランダム化します。NNI移動の数は、パラメータnumで指定されます。

  * `root` : 編集する木の根ノード。
  * `num` : 実行するNNI移動の数。
