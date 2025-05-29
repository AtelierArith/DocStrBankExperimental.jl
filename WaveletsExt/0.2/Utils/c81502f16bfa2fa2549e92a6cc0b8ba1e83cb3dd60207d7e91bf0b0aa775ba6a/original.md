```
getleaf(tree, tree_type)
```

Returns the leaf nodes of a tree.

# Arguments

  * `tree::BitVector`: BitVector to represent binary tree.

# Returns

`::BitVector`: BitVector that can represent a binary tree, but only the leaves are labeled 1, the rest of the nodes are labeled 0.

# Examples

```@repl
using Wavelets, WaveletsExt

tree = maketree(4, 2, :dwt)     # [1,1,0]
getleaf(tree)                   # [0,0,1,1,1,0,0]
```
