```
PreOrderDFS{T,F} <: TreeIterator{T}
```

Iterator to visit the nodes of a tree, guaranteeing that parents will be visited before their children.

Optionally takes a filter function that determines whether the iterator should continue iterating over a node's children (if it has any) or should consider that node a leaf.

e.g. for the tree

```
Any[Any[1,2],Any[3,4]]
├─ Any[1,2]
|  ├─ 1
|  └─ 2
└─ Any[3,4]
   ├─ 3
   └─ 4
```

we will get `[[[1, 2], [3, 4]], [1, 2], 1, 2, [3, 4], 3, 4]`.
