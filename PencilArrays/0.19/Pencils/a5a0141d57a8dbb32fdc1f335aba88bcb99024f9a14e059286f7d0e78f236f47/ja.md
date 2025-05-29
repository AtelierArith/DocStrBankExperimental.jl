```
range_remote(p::Pencil, coords, [order = LogicalOrder()])
range_remote(p::Pencil, n::Integer, [order = LogicalOrder()])
```

与えられたMPIプロセスが保持するデータ範囲を取得します。

最初のバリアントでは、`coords`は直交トポロジーにおけるMPIプロセスの座標です。これらはタプル`(i, j, ...)`として指定することも、`CartesianIndex`として指定することもできます。

2番目のバリアントでは、`n`はトポロジー内の特定のプロセスの線形インデックスです。
