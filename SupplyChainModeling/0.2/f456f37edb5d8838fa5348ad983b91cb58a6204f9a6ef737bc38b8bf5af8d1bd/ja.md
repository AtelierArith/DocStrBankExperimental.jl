```
add_product!(plant::Plant, product::Product; bill_of_material::Dict{Product, Float64}, unit_cost, maximum_throughput)
```

プラントが製品を生産できることを示します。

キーワード引数は次のとおりです：

  * `bill_of_material`: 製品の1単位を生産するために必要な他の製品の量。この辞書は、他の製品が必要ない場合は空であっても構いません。
  * `unit_cost`: 製品の1単位を生産するためのコスト。
  * `maximum_throughput`: 一定期間内に生産できる製品の最大量。
  * `time`: 生産リードタイム。
