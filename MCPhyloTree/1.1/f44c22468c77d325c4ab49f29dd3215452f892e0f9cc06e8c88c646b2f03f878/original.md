```
NNI!(root::T)::Int64  where T<:AbstractNode
```

This function does a nearest neighbour interchange (NNI) move on the tree specified by `root`. The target is identified by the number of the target node.

The function returns 1 if the move was successful and 0 else.

  * `root` : root node of tree on which to perform the NNI.
