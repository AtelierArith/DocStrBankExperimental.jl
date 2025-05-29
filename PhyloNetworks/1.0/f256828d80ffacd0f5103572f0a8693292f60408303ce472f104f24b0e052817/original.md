```
shrink3cycles!(net::HybridNetwork, unroot::Bool=false)
```

Remove all 2- and 3-cycles from a network.

Return true if `net` contains a 2-cycle or a 3-cycle; false otherwise. A 3-cycle (2-cycle) is a set of 3 (2) nodes that are all connected. One of them must be a hybrid node, since `net` is a DAG.

If `unroot` is false and the root is up for deletion, it will be kept only if it is has degree 2 or more. If `unroot` is true and the root is up for deletion, it will be kept only if it has degree 3 or more. A root node with degree 1 will be deleted in both cases.

See [`shrink3cycleat!`](@ref) for details on branch lengths and inheritance values.
