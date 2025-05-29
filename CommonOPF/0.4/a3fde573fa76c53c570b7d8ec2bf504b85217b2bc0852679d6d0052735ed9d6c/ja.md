```
init_split_networks!(mg::MetaGraphsNext.MetaGraph; init_vs::Dict = Dict())
```

`mg`の`:load_sum_order`を使用して、正しい順序で`init_split_networks!`を実行します。つまり、負荷を葉 - 変電所接続で、すべての負荷の合計（および変電所での電圧）として設定します。
