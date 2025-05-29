```
reordermesh(fens, fes, ordering)
```

Reorder mesh (reshuffle nodes, renumber connectivities correspondingly).

# Arguments

  * `fens`: The set of mesh nodes.
  * `fes`: The set of elements.
  * `ordering`: The desired ordering of the nodes and elements.

# Returns

The reordered mesh nodes and elements.

The ordering may come from Reverse Cuthill-McKey (package SymRCM).
