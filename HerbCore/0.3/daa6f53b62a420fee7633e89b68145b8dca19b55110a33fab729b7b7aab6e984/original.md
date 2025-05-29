```
node_depth(root::AbstractRuleNode, node::AbstractRuleNode)::Int
```

Return the depth of `node` for an [`AbstractRuleNode`](@ref) tree rooted at `root`. Depth is `1` when `root == node`.

!!! warning
    `node` must be a subtree of `root` in order for this function to work.

