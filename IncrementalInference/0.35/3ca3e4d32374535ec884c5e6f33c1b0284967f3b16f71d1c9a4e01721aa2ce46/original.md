```julia
getAllTrees(fg)

```

Deterministically get all trees associated with all possible variable orderings of `dfg` factor graph. Returns a dictionary with (tree, ordering, nnz) tuples.

Warning: factorial number of possibilities, so use carefully!
