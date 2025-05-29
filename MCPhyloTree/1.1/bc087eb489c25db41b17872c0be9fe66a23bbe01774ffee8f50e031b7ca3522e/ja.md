```
function add_child!(mother_node::N, child::N, child_position::Int64)::Nothing where N <: GeneralNode
```

この関数は母ノードに子ノードを追加します。母ノードのアリティは `1` 増加し、子ノードのルートステータスは `False` に設定されます。

  * `mother_node` : 子ノードを追加するノード。
  * `child` : mother_node.children に追加するノード。
  * `child_position` : 新しい子ノードを追加するインデックス。
