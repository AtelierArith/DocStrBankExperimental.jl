```
struct HEOMSuperOp
```

General HEOM superoperator matrix.  

# Fields

  * `data` : the HEOM superoperator matrix
  * `dimensions` : the dimension list of the coupling operator (should be equal to the system dimensions).
  * `N` : the number of auxiliary density operators
  * `parity`: the parity label (`EVEN` or `ODD`).

!!! note "`dims` property"
    For a given `M::HEOMSuperOp`, `M.dims` or `getproperty(M, :dims)` returns its `dimensions` in the type of integer-vector.

