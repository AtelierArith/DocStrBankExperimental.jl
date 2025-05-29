```
mutable struct TreeNode{T <: TreeNodeData}
```

Structural information on the tree, *i.e.* topology and branch length.

  * `anc::Union{Nothing,TreeNode}`: Ancestor
  * `child::Array{TreeNode,1}`: List of children
  * `isleaf::Bool`
  * `isroot::Bool`
  * `tau::Union{Missing, Float64}`
  * `data::T`
