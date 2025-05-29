```
XPRSaddcboptnode(prob, cb, priority)
```

# 引数

  * `cbprob`: コールバック関数 `optnode` に渡される問題。
  * `infeasible`: 実現可能性の状態。ユーザーによって非ゼロの値が設定された場合、現在のノードは非実現可能と見なされます。

`cb` は次のシグネチャで呼び出されます：

```
cb(cbprob)::infeasible
```
