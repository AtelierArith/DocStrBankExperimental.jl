```
NNI(root::T, target::T, lor::Bool)::Int64   where T<:AbstractNode
```

This function does a nearest neighbour interchange (NNI) move on the tree specified by `root`. The parameter `target` specifies the node which performs the interchange move using the left or right child of the target node. If the left child should be used `lor=true`.

The function returns 1 if the move was successful and 0 else.

  * `root` : root node of tree on which to perform the NNI.
  * `target` : specific node of tree to interchange.
  * `lor` : Bool; "true" uses the left child of `target,` "false," the right child.
