```
removenode!(g::Game, node::GameNode = g.node)
```

Remove a node (by default, the current node) in a `Game`, and go to the parent node.

All children of the node are also recursively deleted.
