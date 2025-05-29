```
findnodematching(node::GameNode, pred)
findnodematching(g::Game, pred)
```

ゲームツリー内で述語 `pred` を満たすノードを見つけます。

`GameNode` を返すか、ツリー内に `pred` を満たすノードがない場合は `nothing` を返します。
