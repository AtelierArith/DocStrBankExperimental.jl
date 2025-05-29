```
SearchOrder
```

Abstract type representing the order of processing during a branch and prune search.

For custom search orders following methods must be implemented:

  * `pop!(so::SearchOrder)`: return the next leaf to be processed.   Return `nothing` when the search is done.
  * `push!(so::SearchOrder, leaf::BPNode)`: add a leaf to the set of leaves to be   processed.

The object is initialized by giving it the root node of the search tree, as `SearchOrder(root::BPNode)`.
