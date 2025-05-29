```
KnnResult(ksearch::Integer)
```

Creates a priority queue with fixed capacity (`ksearch`) representing a knn result set. It starts with zero items and grows with [`push_item!`](@ref) calls until `ksearch` size is reached. After this only the smallest items based on distance are preserved.
