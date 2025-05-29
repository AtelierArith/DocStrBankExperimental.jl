```
associate_matrix!(mumps, n, irow, jcol, vals)
```

Register the sparse matrix given in coordinate format with the `Mumps` object `mumps`. This function makes it possible to define the matrix on the host only. If the matrix is defined on all nodes, there is no need to use this function.
