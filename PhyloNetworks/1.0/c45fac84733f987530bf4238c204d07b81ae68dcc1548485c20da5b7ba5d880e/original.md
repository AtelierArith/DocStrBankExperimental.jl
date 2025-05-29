```
blobdecomposition!(network)
blobdecomposition(network)
```

Find blobs using [`biconnectedcomponents`](@ref); find their roots using [`blobinfo`](@ref); create a forest in the form of a disconnected network (for efficiency), by deconnecting the root of each non-trivial blob from its parent. The root of each blob corresponds to a new leaf (in another tree of the forest): the number of the blob's root is given to the newly created leaf.

The first (bang) version modifies the network and returns the array of blob roots. The second version copies the network then returns a tuple: the forest and the array of blob roots.

Warnings:

  * the forest is represented by a single HybridNetwork object, on which most functions don't work (like `writenewick`, plotting etc.) because the network is disconnected (to make the forest). Revert back to low-level functions, e.g. `printedges` and `printnodes`.
  * see [`biconnectedcomponents`](@ref) for node attributes modified during the algorithm.
