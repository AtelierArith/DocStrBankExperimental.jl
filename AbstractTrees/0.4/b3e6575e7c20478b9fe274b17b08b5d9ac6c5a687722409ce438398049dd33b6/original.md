```
PostOrderDFS{T} <: TreeIterator{T}
```

Iterator to visit the nodes of a tree, guaranteeing that children will be visited before their parents.

e.g. for the tree

```
Any[1,Any[2,3]]
├─ 1
└─ Any[2,3]
   ├─ 2
   └─ 3
```

we will get `[1, 2, 3, [2, 3], [1, [2, 3]]]`.
