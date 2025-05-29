```
traversal([f], tree, style=:postorder; internals, leaves, root)
traversal([f], node, style=:postorder; internals, leaves, root)
```

Iterate through nodes of `tree` according to `style`, skipping nodes for which `f` returns `false`. `style` must be in `collect(keys(TreeTools.traversal_styles))`. For now its just `:postorder`.

See `postorder_traversal` for extended docstring.
