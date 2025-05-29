```
root!(tree::Tree, node::AbstractString; root_on_leaf, time=0., remove_singletons=true)
```

Root `tree` at `tree.lnodes[node]`. Equivalent to outgroup rooting. If `time` is non-zero, root above `node` at height `time`, inserting a new node.

If `remove_singletons`, singleton nodes are removed after re-rooting. This is useful to remove the old root, which often ends up being a singleton.
