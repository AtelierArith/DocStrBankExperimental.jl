```
make_halo(delta, inner_delta=nothing; only_layers=[], ignore_layers=[])
```

`GeometryStructure` ハローを生成するための関数 `(c)->halo(c, delta, inner_delta; only_layers, ignore_layers)` を返します。

`ignore_layers` にあるレイヤーのエンティティはスキップされます。`only_layers` が空でない場合、ハローを生成するためにそのレイヤーのみが使用されます。含めるレイヤーと除外するレイヤーは、レイヤー名 `Symbol` として提供することができ、その場合はレイヤー名のみが一致する必要があります。または、完全な `DeviceLayout.Meta` オブジェクトとして提供することもでき、その場合はすべてのメタデータフィールド（例：`SemanticMeta` のインデックスとレベル）が一致する必要があります。
