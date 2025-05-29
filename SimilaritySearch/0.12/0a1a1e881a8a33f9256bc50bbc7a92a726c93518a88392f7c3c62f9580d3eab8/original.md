```
ParallelExhaustiveSearch(; dist=SqL2Distance(), db=VectorDatabase{Float32}())
```

Solves queries evaluating `dist` in parallel for the query and all elements in the dataset. Note that this should not be used in conjunction with `searchbatch(...; parallel=true)` since they will compete for resources.
