```
knn(tree::NNTree, points, k [, sortres=false]) -> indices, distances
```

Performs a lookup of the `k` nearest neigbours to the `points` from the data in the `tree`. `skip` is an optional predicate to determine if a point that would be returned should be skipped based on its index.

See also: `knn!`, `nn`.
