```
IndexedChildren <: ChildIndexing
```

Indicates that the object returned by `children(n)` where `n` is a tree node is indexable (1-based).

If a node has this trait so must all connected nodes in the tree.  Otherwise, use `NonIndexedChildren()` instead.

## Required Methods

  * A node `node` with this trait must return an indexable object from `children(node)`.
