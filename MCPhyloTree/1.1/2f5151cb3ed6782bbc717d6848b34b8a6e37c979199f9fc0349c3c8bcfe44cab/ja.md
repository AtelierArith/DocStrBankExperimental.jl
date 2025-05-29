```
prune_tree!(root::T, node_names::Vector{T})::Nothing where T<:AbstractNode
```

プルーニングツリーのインプレースバージョン。

  * `root` : プルーニングするツリーのルートノード。
  * `node_names`: ツリーから削除されるノードオブジェクトのベクター。
