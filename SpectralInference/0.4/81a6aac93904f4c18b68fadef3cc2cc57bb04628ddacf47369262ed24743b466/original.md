```
as_polytomy!(f::Function, tree)
```

in-place removal of nodes. function `f` should return `true` if the node is to be removed. Children of node are attached to the parent of the removed node
