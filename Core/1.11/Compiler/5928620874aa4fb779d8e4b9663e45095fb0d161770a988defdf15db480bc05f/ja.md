```
postdominates(domtree::PostDomTree, bb1::Int, bb2::Int) -> Bool
```

`bb1`が`bb2`をポスト支配しているかどうかをチェックします。`bb1`と`bb2`は`CFG`ブロックへのインデックスです。`bb1`が`bb2`をポスト支配しているのは、`bb2`から出口へのすべての経路が`bb1`を経由する場合です。（他のブロックが間に入ることもあります。例：`bb2->bbx->bb1->exit`）。
