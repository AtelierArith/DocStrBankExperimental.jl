```
CacheSaveJLD2(p::AbstractProblem{T}, filename::String, dataset::String="cache_costs") where T
```

Save the costs from the cache to a JLD2 file with the name `filename` and to the dataset `dataset`. The default dataset is named 'cache_costs'. It is possible to write to multiple datasets in one file, however, datasets cannot be overwritten.
