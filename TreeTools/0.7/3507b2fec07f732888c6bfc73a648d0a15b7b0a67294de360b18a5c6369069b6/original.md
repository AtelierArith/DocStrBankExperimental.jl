```
nodes(t; skiproot=false)
leaves(t)
internals(t; skiproot=false)
```

Iterator over all nodes / leaves / internal nodes of a tree. If `skiproot`, the root node will be skipped by the iterator.

# Note

`length` cannot be called on `internals(t)` as the latter is based on `Iterators.filter`.   A way to get the number of internal nodes of a tree is for example by calling   `length(nodes(t)) - length(leaves(t))`.
