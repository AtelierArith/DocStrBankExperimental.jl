```
DeferredFuture(pid::Integer=myid()) -> DeferredFuture
```

プロセス `pid` に `DeferredFuture` を作成します。デフォルトの `pid` は現在のプロセスです。

`DeferredFuture` 内のデータは、依然として `put!` された場所にあります。`pid` 引数は、そのデータへの最外部参照がどこにあるかを制御します。
