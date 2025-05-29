```
random_region_graph(X::AbstractVector, depth::Int = 5, replicas::Int = 2, num_splits::Int = 2)
```

  * `X`: Vector of all variables to include; for the root region
  * `depth`: how many layers to do splits
  * `replicas`: number of replicas or paritions (replicas only used for the root region; for other regions only 1 parition (inner nodes), or 0 parition for leaves)
  * `num_splits`: number of splits for each parition; split variables into random equaly sized regions
