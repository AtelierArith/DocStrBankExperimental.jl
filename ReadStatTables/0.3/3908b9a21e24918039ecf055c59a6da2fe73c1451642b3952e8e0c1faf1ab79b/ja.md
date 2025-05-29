```
metastyle!(tb::ReadStatTable, key::Union{Symbol, AbstractString}, style::Symbol)
```

テーブル `tb` に対して、`key` に関連付けられたすべてのメタデータのスタイルを `style` に設定します。

メタデータのスタイルは `key` のみによって決定されるため、異なる列間で区別されません。
