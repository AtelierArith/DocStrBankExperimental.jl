```
DeferredChannel(pid::Integer=myid(), num::Integer=1; content::DataType=Any) -> DeferredChannel
```

特定のサイズと型のリモートチャネルへの参照を持つ `DeferredChannel` を作成します。f() は、`pid` で実行されると `AbstractChannel` の実装を返さなければならない関数です。

デフォルトの `pid` は現在のプロセスです。
