```
StatelessBFS{T} <: TreeIterator{T}
```

Iterator to visit the nodes of a tree, all nodes of a level will be visited before their children

This iterator requires [`getdescendant`](@ref) to be valid for all nodes in the tree, but the nodes do not necessarily need the [`IndexedChildren`](@ref) trait.

e.g. for the tree

```
Any[1,Any[2,3]]
├─ 1
└─ Any[2,3]
   ├─ 2
   └─ 3
```

we will get `[[1, [2,3]], 1, [2, 3], 2, 3]`.

WARNING: This is $O(n^2)$, only use this if you know you need it, as opposed to a more standard stateful approach.
