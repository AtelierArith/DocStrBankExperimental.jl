```
getdescnames(tree::AbstractTree, mrca::Int) :: Vector{String}
getdescnames(tree::AbstractTree) :: Vector{Vector{String}}
```

Find the names of all tip descendents from a common ancestor node, or such  descendent name lists for all nodes of the tree.
