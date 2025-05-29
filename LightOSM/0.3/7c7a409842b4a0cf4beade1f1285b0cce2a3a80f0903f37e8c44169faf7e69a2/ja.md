```
restriction_cost_adjustment(g::OSMGraph)
```

制限のためのコスト調整関数（dijkstraおよびastarで使用）を返します。返される関数は3つの引数を取ります。`u`は現在のノード、`v`は隣接ノード、`parents`は親dijkstra状態の配列です。デフォルトでは、`g.indexed_restrictions`が使用され、`parents`内のすべての前のノードを考慮して、`u`から`v`への経路が制限されているかどうかを確認します。
