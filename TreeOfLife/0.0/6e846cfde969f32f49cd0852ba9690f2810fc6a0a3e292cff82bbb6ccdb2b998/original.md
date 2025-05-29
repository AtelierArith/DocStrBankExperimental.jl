```
getsubtree(oldtree::AbstractTree, tipset; 
	simplify::Bool=true, keeproot::Bool=false) :: AbstractTree
```

Extract the subtree generated from a given set of tips of the tree. 

The argument `simplify` controls whether internal node with only one child  needs to be reduced, i.e., connecting directly its child and its parent; by  default it is set to `true`. 

The argument `keeproot` controls whether the original root node needs to be  contained in the subtree; by default it is set to `false`, in other words,  yielding a truly minimum spanning tree (MST). 

When `simplify` is set to `false`, the value of `keeproot` has no effect.
