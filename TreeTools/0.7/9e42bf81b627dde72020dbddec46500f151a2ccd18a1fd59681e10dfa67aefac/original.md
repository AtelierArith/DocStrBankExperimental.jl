```
abstract type TreeNodeData
```

Abstract supertype for data attached to the `dat` field of `TreeNode` objects. Implemented concrete types are

  * `EmptyData`: empty struct. Use if you do not have to attach data to nodes.
  * `MiscData`: contains a dictionary for attaching extra data to nodes. Also behaves like  a `Dict` for indexing/iterating, *e.g.* `x.dat[key] == x[key]`.
