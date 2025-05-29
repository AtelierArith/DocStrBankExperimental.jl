```
mutable struct TreeNode{T <: TreeNodeData}
```

木の構造情報、すなわちトポロジーと枝の長さ。

  * `anc::Union{Nothing,TreeNode}`: 祖先
  * `child::Array{TreeNode,1}`: 子のリスト
  * `isleaf::Bool`
  * `isroot::Bool`
  * `tau::Union{Missing, Float64}`
  * `data::T`
