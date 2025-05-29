```
XPRSaddcbnewnode(prob, cb, priority)
```

# 引数

  * `cbprob`: コールバック関数 `newnode` に渡される問題。
  * `parentnode`: 新しいノードの親の一意の識別子。
  * `node`: 新しいノードに割り当てられた一意の識別子。
  * `branch`: `parentnode` の子ノードの中での新しいノードのシーケンス番号。MIP エンティティの通常のブランチの場合、これは `0` または `1` になります。

`cb` は次のシグネチャで呼び出されます：

```
cb(cbprob, parentnode, node, branch)::Nothing
```
