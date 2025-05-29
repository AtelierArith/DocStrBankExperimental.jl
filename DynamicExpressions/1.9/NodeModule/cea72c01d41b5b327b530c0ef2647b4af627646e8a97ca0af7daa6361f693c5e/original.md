```
copy_node(tree::AbstractExpressionNode; break_sharing::Val{BS}=Val(false)) where {BS}
```

Copy a node, recursively copying all children nodes. This is more efficient than the built-in copy.

If `break_sharing` is set to `Val(true)`, sharing in a tree will be ignored.
