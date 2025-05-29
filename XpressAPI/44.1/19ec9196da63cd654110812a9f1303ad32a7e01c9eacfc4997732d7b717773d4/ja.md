```
XPRSaddcbchgnode(prob, cb, priority)
```

# 引数

  * `cbprob`: コールバック関数 `chgnode` に渡される問題。
  * `node`: オプティマイザによって選択されたノードの番号へのポインタ。この値は変更できません。

`cb` は次のシグネチャで呼び出されます：

```
cb(cbprob)::node
```
