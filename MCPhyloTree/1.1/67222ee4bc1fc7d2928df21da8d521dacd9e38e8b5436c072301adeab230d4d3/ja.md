```
delete_node!(node::T)::Nothing where T<:AbstractNode
```

この関数は、ツリーからノードを削除し、そのすべての子ノードを親ノードに割り当てます。

  * `node` : 削除されるノード。
