```
remove_child!(mother_node::N, left::Bool)::N where N <: GeneralNode
```

この関数は、このノードの娘であるノードのリストから子ノードを削除します。"True"の入力は左の子を削除し、"False"は右の子を削除します。

削除されたノードを返します。

  * `mother_node` : 子を削除するノード。
  * `left` : mother_nodeのどの子を削除するかを決定するブール値。
