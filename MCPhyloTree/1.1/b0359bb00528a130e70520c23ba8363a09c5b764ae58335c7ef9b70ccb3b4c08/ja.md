```
function create_tree_from_leaves(leaf_nodes::Vector{String}, rooted::Bool=false<:AbstractNode
```

葉の名前のリストからランダムな木を構築します。デフォルトでは木は根なしです。

新しい木の根ノードを返します。

  * `leaf_nodes` : 葉の名前として使用される文字列のリスト。
  * `rooted` : 木が根付きであるべきかどうかを示すブール値。
