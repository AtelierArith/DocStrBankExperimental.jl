```
randomize(root::T, num::Int64=100)::T where T <:AbstractNode
```

This function returns a randomized copy of the tree by performing a number of nearest neighbour interchange (NNI) moves and a randomization of the branch lengths. The number of NNI moves is specified in the parameter num. 

  * `root` : root node of tree to be edited.
  * `num` : amount of NNI moves to perform.
