```
rebuild(g::SearchGraph; context=SearchGraphContext())
```

Rebuilds the `SearchGraph` index but seeing the whole dataset for the incremental construction, i.e., it can connect the i-th vertex to its knn in the 1..n possible vertices instead of its knn among 1..(i-1) as in the original algorithm.

# Arguments

  * `g`: The search index to be rebuild.
  * `context`: The context to run the procedure, it can differ from the original one.
  * `minbatch`: controls how the multithreading is made, see [`getminbatch`](@ref)
