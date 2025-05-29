```
prune_tree(root::T, node_names::Vector{String})::T where T<:AbstractNode
```

この関数は、特定のノードとその子孫をツリーから削除します。

  * `root` : プルーニングするツリーのルートノード。
  * `node_names` : 削除するノードを指定するために使用される文字列のベクター。
