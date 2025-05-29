```
postorder_traversal([f], tree; root=true, leaves=true, internals=true)
```

Traverse `tree` in postorder, iterating over nodes. The children of `node` are returned in the same order as `children(node)`.

Keep only nodes `n` such that `f(n)` is true. If `leaves`, `internals` or `root` are set to `false`, the corresponding nodes are excluded.

## Examples

```julia
for node in postorder_traversal(tree; root=false)
    isroot(node) # always false
end

[label(x) for x in postorder_traversal(tree; internals=false)] # labels of leaf nodes
```
