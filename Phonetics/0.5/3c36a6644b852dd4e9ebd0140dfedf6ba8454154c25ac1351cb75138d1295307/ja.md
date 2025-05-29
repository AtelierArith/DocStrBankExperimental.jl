```
nneighbors(tree::TextVPTree, query, n)
```

与えられたクエリ `query` に対して、VPツリー `tree` から `n` 個の最近傍を見つけます。

# 戻り値

  * アイテム自体がキーで、アイテムから `query` までの距離が値である `PriorityQueue`。`PriorityQueue` は、小さい値が大きい値よりも高い優先度を持つように定義されています。
