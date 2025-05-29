```
index_mapped_groups(order::Int, model::ABM; scheduler = Schedulers.ByID)
index_mapped_groups(order::Int, model::ABM, filter::Function; scheduler = Schedulers.ByID)
```

Return an iterable of agent ids in the model, meeting the `filter` criteria if used.
