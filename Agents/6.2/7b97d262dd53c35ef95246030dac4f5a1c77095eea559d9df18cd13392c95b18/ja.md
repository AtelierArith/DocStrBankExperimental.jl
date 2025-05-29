```
index_mapped_groups(order::Int, model::ABM; scheduler = Schedulers.ByID)
index_mapped_groups(order::Int, model::ABM, filter::Function; scheduler = Schedulers.ByID)
```

モデル内のエージェントIDのイテラブルを返し、`filter`基準を満たす場合はそれを使用します。
