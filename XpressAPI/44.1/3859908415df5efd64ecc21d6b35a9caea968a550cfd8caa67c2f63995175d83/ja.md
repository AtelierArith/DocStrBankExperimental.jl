```
XPRSaddcbmipthread(prob, cb, priority)
```

# 引数

  * `cbprob`: コールバック関数に渡される問題。
  * `threadprob`: MIPスレッドの問題ポインタ

`cb`はこのシグネチャで呼び出されます：

```
cb(cbprob, threadprob)::Nothing
```
