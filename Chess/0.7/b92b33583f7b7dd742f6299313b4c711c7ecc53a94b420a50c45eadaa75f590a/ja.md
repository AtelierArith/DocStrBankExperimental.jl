```
removeallchildren!(g::Game, node::GameNode = g.node)
```

ゲーム内の指定されたノードのすべての子を再帰的に削除します。

ノードが指定されていない場合は、現在のノードの子を削除します。
