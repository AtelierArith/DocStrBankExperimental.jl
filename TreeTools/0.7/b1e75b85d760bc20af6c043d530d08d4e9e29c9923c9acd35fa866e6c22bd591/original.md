```
root!(tree; method=:midpoint, topological = false)
```

Root tree using `method`. Only implemented method is `:midpoint`. 

# Methods

## `:midpoint`

Distance between nodes can be either topological (number of branches) or based on branch length. Does not create a polytomy at the root: if the midpoint is an already existing internal node (not the root), creates a new root node at infinitesimal distance below it.

Midpoint rooting will exit without doing anything if

  * the distance between the two farthest leaves is `0`. This happens if all branch lengths  are 0.
  * the current root is already the midpoint.

## `:model`

Provide keyword argument `model::Tree`. Try to root `tree` like `model`. If the two trees only differ by rooting, they will have the same topology at the end of this. Else, tree will be rerooted but a warning will be given.
