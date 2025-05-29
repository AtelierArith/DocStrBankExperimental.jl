```
halo(cs::CoordinateSystem, outer_delta, inner_delta=nothing; only_layers=[],
    ignore_layers=[])
halo(cs::Cell, outer_delta, inner_delta=nothing; only_layers=[], ignore_layers=[])
```

`cs`のすべてのエンティティに対してハローを持つ`typeof(cs)`型の座標系で、`cs.refs`を通じてトレースします。

`ignore_layers`のレイヤーにあるエンティティはスキップされます。`only_layers`が空でない場合、ハローを生成するためにそのレイヤーのみが使用されます。含めるレイヤーと除外するレイヤーは、レイヤー名`Symbol`として提供できます。この場合、レイヤー名のみが一致する必要があります。または、完全な`DeviceLayout.Meta`オブジェクトとして提供することもでき、その場合はすべてのメタデータフィールド（例：`SemanticMeta`のインデックスとレベル）が一致する必要があります。

ポリゴンの向きは一貫している必要があり、外側のポリゴンは同じ向きを共有し、穴は反対の向きを持つ必要があります。さらに、穴は外側のポリゴン内に含まれている必要があります。穴のエッジをオフセットすると、コーナーで正のアーティファクトが生成される可能性があります。
