```
remove_child!(mother_node::N, child::N)::N where N<:AbstractNode
```

この関数は、このノードの娘であるノードのリストから子ノードを削除します。

削除されたノードが返されます。

  * `mother_node` : 子ノードを削除するノード。
  * `child` : 削除する特定のノード。このノードは `mother_node` の子でなければなりません。
