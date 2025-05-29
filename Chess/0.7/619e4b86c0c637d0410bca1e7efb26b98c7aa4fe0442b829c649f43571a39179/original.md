```
GameNode
```

Type representing a node in a `Game`.

Game can contain variations, so this type actually represents a node in a tree-like structure.

A `GameNode` is a mutable struct with the following slots:

  * `parent`: The parent `GameNode`, or `nothing` if this node is the root of the game.
  * `board`: The board position at this node.
  * `children`: A vector of `GameNode`s, the children of the current node. The first entry is the main continuation, the remaining entries are alternative variations.
  * `data`: A `Dict{String, Any}` used to store information about this node. This is used for comments and numeric annotation glyphs, but can also be used to store other data.
  * `id`: An `Int`, used to look up this node in a `Game`, which contains a dictionary mapping ids to `GameNode`s.
