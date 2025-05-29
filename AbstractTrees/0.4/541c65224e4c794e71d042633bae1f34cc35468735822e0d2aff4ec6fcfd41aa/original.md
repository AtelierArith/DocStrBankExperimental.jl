```
Leaves{T} <: TreeIterator{T}
```

Iterator to visit the leaves of a tree, e.g. for the tree

```
Any[1,Any[2,3]]
├─ 1
└─ Any[2,3]
   ├─ 2
   └─ 3
```

we will get `[1,2,3]`.
