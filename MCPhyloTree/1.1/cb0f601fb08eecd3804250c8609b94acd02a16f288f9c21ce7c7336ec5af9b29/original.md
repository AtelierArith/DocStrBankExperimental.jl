```
NNI(root::T)::T  where T<:AbstractNode
```

This function does a nearest neighbour interchange (NNI) move on the tree specified by `root.`

Returns a mutated copy while leaving the original tree intact.

  * `root` : root node of tree on which to perform the NNI.
