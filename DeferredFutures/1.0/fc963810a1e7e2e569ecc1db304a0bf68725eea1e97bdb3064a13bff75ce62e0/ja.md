```
DeferredChannel(pid::Integer=myid(), num::Integer=1; content::DataType=Any) -> DeferredChannel
```

`DeferredChannel`を作成します。デフォルトの`pid`は現在のプロセスです。初期化されると、`DeferredChannel`はプロセス`pid`上の`Channel{content}(num)`を参照します。

`DeferredChannel`内のデータは、最初のデータが`put!`された場所に依然として存在することに注意してください。`pid`引数は、そのデータへの最外部の参照がどこにあるかを制御します。
