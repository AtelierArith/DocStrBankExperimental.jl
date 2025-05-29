```
add_product!(storage::Storage, product; initial_inventory::Real=0, 
                                        unit_handling_cost::Real=0,
                                        unit_holding_cost::Real=0, 
                                        maximum_throughput::Float64=Inf, 
                                        additional_stock_cover::Real=0.0)
```

ストレージが製品を保管できることを示します。

キーワード引数は次のとおりです：     - `initial_inventory`: ストレージの場所に最初にある製品の量     - `unit_handling_cost`: ストレージの場所での製品1単位の取り扱いコスト     - `unit_holding_cost`: ストレージの場所での製品1単位の保管コスト（期間あたり）     - `maximum_throughput`: 期間あたりに送信できる製品の最大単位数
