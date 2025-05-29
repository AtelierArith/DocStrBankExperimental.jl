```
as_polytomy(f::Function, tree)
```

Makes a copy of the tree, then removes nodes. function `f` should return `true` if the node is to be removed. Children of node are attached to the parent of the removed node
