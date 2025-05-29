```
removenode!(g::Game, node::GameNode = g.node)
```

`Game`内のノード（デフォルトでは現在のノード）を削除し、親ノードに移動します。

ノードのすべての子も再帰的に削除されます。
