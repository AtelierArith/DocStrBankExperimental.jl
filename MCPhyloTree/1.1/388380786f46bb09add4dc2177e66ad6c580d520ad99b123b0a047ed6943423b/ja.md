```
prune_tree!(root::T, node_names::Vector{String})::Nothing where T<:AbstractNode
```

木を剪定するインプレースバージョン。

  * `root` : 剪定する木のルートノード。
  * `node_names` : 削除するノードを指定するために使用される文字列のベクター。
