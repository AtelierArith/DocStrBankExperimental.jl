```
function receive(fn::Function, pd::Process)
```

`pd`プロセスに配信されるすべてのメッセージ`msg`に対して`fn(msg)`を実行します。

`Shutdown`制御メッセージが受信された場合は戻ります。
