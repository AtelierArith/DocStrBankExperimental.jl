```
compute_boundary_trans(d::DataDomain, perm)
```

Compute the boundary half face transmissibilities for perm. The input `perm` can either be the symbol of some data defined on `Cells()`, a vector of numbers for each cell or a matrix with number of columns equal to the number of cells.
