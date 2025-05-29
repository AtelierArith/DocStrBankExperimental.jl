```
polyneigh(P, criterion = :Queen)
```

Build a spatial weights object from a vector of polygons `P`.

# Optional Arguments

  * `criterion=:Queen`: neighbour criterion. `:Queen` or `:Rook`.
  * `tol=0.0`: tolerance for polygon contiguity.
