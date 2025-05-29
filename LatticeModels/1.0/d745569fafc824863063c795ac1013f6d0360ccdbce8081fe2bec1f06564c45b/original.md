```
coordoperator(sys, crd)
coordoperator(basis, crd)
coordoperator(lat[, internal], crd)
```

Generate a coordinate operator for the given lattice.

## Arguments

  * `sys`: a `System` for which the coordinate operators are to be generated.
  * `basis`: a one-particle `Basis` for which the coordinate operators are to be generated.
  * `lat`: a lattice for which the coordinate operators are to be generated.
  * `internal`: The basis for the internal degrees of freedom.
  * `crd`: The coordinate to generate the operator for. Must be an integer representing the   coordinate index (e. g. `1` for x, `2` for y, etc.) or a symbol (e. g. `:x`, `:y`, etc.).
