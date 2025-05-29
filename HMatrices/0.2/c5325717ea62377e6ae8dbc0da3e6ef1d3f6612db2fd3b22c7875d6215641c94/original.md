```
ClusterTree(elements,splitter;[copy_elements=true, threads=false])
```

Construct a `ClusterTree` from the  given `elements` using the splitting strategy encoded in `splitter`. If `copy_elements` is set to false, the `elements` argument are directly stored in the `ClusterTree` and are permuted during the tree construction.
