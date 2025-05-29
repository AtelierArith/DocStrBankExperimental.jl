```
polyneigh(A, criterion = :Queen)
```

Build a spatial weights object from table A that contains a geometry column.

# Optional Arguments

  * `criterion=:Queen`: neighbour criterion. `:Queen` or `:Rook`.
  * `tol=0.0`: tolerance for polygon contiguity.
