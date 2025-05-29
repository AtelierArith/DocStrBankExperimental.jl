```
wikidata_minerals()::Dict{String, Material}
```

ウィキデータの鉱物に関するSPARQLクエリに基づく鉱物データ。明確に定義された組成を持つ鉱物のみが含まれています。レプリカは除外されました。

また、`:Class`、`:Formula`、および `:Description` プロパティも含まれています。
