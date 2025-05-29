```
@onprocs procsel expr
```

`expr`を`procsel`のすべてのプロセスで並列に実行します。すべてのプロセスが完了するまで待機します。すべての結果をベクターとして返します（または、`procsel`自体がスカラー値の場合は単一のスカラー値として返します）。

例:

```julia
using Distributed
addprocs(2)
workers() == @onprocs workers() myid()
```
