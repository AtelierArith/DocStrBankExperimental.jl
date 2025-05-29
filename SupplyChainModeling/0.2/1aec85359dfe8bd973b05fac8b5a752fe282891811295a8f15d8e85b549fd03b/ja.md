```
add_product!(supplier::Supplier, product::Product; unit_cost::Float64, maximum_throughput::Float64)
```

サプライヤーが製品を提供できることを示します。

キーワード引数は次のとおりです：

  * `unit_cost`: このサプライヤーからの製品の単位あたりのコスト。
  * `maximum_throughput`: 各時間単位で提供できる最大ユニット数。
