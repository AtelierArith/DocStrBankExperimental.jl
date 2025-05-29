```
adjacency_list(g::AGraph)
adjacency_list(g::ADiGraph, dir=:out)
```

Returns the adjacency list `a` of a graph (a vector of vector of ints). The `i`-th element of the adjacency list is a vector containing the neighbors of `i` in `g`.

For directed graphs a second optional argument can be specified (`:out` or `:in`). The neighbors in the returned adjacency list are considered accordingly as those related through outgoing or incoming edges.

The elements of  `a[i]` have the same order as in the iterator `(out_/in_)neighbors(g,i)`.

*Attention*: For some graph types it returns a reference, not a copy, therefore the returned object should not be modified.
