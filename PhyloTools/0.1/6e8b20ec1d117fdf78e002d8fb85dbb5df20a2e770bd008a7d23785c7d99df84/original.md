```
nwstr(n::Node{I,N}; internal=false)
```

Generate a newick tree string for the tree rooted in `n`. To make this work, `N` (the type of `n.data`) should implement `name()` and `distance()` methods, and optionally `support()`. If `support` is implemented for the data type and it is not NaN, it will supersede `name` for the labeling of internal nodes. See for instance the `NewickData` type.
