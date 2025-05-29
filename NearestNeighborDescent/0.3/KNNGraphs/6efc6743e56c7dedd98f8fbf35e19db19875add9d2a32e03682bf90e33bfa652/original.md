```
HeapKNNGraph(data, metric, indices, distances)
```

Create a HeapKNNGraph from `KxN` matrices of the indices and distances, where `indices[i, v]` and `distances[i, v]` are the index and distance to node `v`s `i`th candidate neighbor. Note that each column of `indices` cannot have duplicate entries, but they need not be sorted by distance.
