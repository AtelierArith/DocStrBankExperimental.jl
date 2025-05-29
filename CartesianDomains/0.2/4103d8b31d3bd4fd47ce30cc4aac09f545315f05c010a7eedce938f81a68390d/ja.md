```
upper_edge_region(full_domain::CartesianIndices, axis::Int, nhalo::Int, nedge::Int)
```

`full_domain` から指定された `axis` に沿って幅 `nedge` の内側の領域の高いエッジに沿ったサブドメインを抽出します。内側の領域は、ハロ領域を含まない `full_domain` 内の領域です。この関数は、指定された幅の内側の領域に沿ったエッジを提供するように設計されています。これは、問題を「中心」のドメインとエッジに沿ったドメインに分割するのに便利です。
