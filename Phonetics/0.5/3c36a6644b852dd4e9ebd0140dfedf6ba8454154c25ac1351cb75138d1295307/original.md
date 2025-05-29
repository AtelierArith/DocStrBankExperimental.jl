```
nneighbors(tree::TextVPTree, query, n)
```

Find the `n` nearest neighbors in a VP tree `tree` to a given query `query`.

# Returns

  * A `PriorityQueue` of items where the keys are the items themselves and the values are the distances from the items to `query`; the `PriorityQueue` is defined such that small values have higher priorities than large ones
