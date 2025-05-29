```
SplitList{T}
```

  * `leaves::Array{T,1}`: labels of leaves
  * `splits::Array{Split,1}`
  * `mask::Array{Bool,1}`: subset of leaves for which splits apply.
  * `splitmap::Dict{T,Split}`: indicate the split corresponding to the branch above a node. Only initialized if built from a tree with labels on internal nodes.

# Constructors

```
SplitList(leaves::Array{T,1}) where T
```

Empty `SplitList`.

```
SplitList(t::Tree[, mask])
```

List of splits in `t`. `mask` defaults to ones.

```
SplitList(r::TreeNode, leaves[, mask])
```

Compute the list of splits below `r`, including `r` itself.   Assume that `r` is part of a tree with `leaves`. `mask` defaults to the set of leaves that are descendents   of `r`.
