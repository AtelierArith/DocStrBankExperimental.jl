```
add_demand!(supply_chain, customer, product, demand::Array{Float64, 1}; service_level=1.0)
```

顧客の製品に対する需要を追加します。需要は各時間帯ごとに指定されます。

キーワード引数は次のとおりです：

  * `service_level`: 需要の比率として許可される失われた販売の数を示します。サービスレベルが1.0の場合、需要は失われることはなく、サービスレベルが0.0の場合、すべての需要が失われる可能性があります。
  * `sales_price`: 製品の単位あたりの販売価格。
  * `lost_sales_cost`: 製品の単位あたりの販売を失うコスト。
