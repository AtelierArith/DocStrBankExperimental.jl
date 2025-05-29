```
nondelaunay(grid;tol=1.0e-14, verbose=true)
```

Return non-Delaunay edges. Returns a vector of tuples: Each tuple consists of `(node1, node2, edge factor, region)`

If the vector has length 0, the grid is boundary conforming Delaunay with respect to each cell region. This means that up to `tol`, all edge form factors are nonnegative.
