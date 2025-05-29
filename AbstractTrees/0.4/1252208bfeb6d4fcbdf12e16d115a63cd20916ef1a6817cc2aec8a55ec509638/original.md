```
TreeCursor{N,P}
```

Abstract type for tree cursors which when constructed from a node can be used to navigate the entire tree descended from that node.

Tree cursors satisfy the abstract tree interface with a few additional guarantees:

  * Tree cursors all have the [`StoredParents`](@ref) and [`StoredSiblings`](@ref) traits.
  * All functions acting on a cursor which returns a tree node is guaranteed to return another `TreeCursor`.   For example, `children`, `parent` and `nextsiblin` all return a `TreeCursor` of the same type as   the argument.

Tree nodes which define `children` and have the traits [`StoredParents`](@ref) and [`StoredSiblings`](@ref) satisfy the `TreeCursor` interface, but calling `TreeCursor(node)` on such a node wraps them in a [`TrivialCursor`](@ref) to maintain a consistent interface.

Note that any `TreeCursor` created from a non-cursor node is the root of its own tree, but can be created from any tree node.  For example the cursor created from the tree `[1,[2,3]]` corresponding to node with value `[2,3]` has no parent and children `2` and `3`.  This is because a cursor created this way cannot infer the iteration state of its siblings.  These constructors are still allowed so that users can run tree algorithms over non-root nodes but they do not permit ascension from the initial node.

## Constructors

All `TreeCursor`s possess (at least) the following constructors

  * `T(node)`
  * `T(parent, node)`

In the former case the `TreeCursor` is constructed for the tree of which `node` is the root.
