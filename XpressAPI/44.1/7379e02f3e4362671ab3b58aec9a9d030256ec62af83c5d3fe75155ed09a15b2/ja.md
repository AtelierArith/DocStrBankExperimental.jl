```
XPRSaddcbnodecutoff(prob, cb, priority)
```

# 引数

  * `cbprob`: コールバック関数 `nodecutoff` に渡される問題。
  * `node`: 切り捨てられたノードのノードID。このIDは、他のコールバックと同様にCURRENTNODE属性から照会することはできません。このコールバックは切り捨てられたノードのコンテキストでは呼び出されないためです。

`cb` は次のシグネチャで呼び出されます：

```
cb(cbprob, node)::Nothing
```
