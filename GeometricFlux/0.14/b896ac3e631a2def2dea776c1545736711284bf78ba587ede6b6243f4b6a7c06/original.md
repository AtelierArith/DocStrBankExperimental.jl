```
LocalPool(aggr, cluster)
```

Local pooling layer.

It pools features with `aggr` operation accroding to `cluster`. It is implemented with `scatter` operation.

# Arguments

  * `aggr`: An aggregate function applied to pool all features.
  * `cluster`: An index structure which indicates what features to aggregate with.
