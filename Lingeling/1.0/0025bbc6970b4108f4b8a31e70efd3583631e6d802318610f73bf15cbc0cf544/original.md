```
lgl_freeze(solver::LglPtr, lit::Integer)
```

Freeze a literal meaning that it will not be eliminated during `lgl_sat` so it can be used in future calls to `lgl_add`.

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.
  * `lit::Integer`: The literal to freeze.

# Throws

  * `InexactError`: If the literal can not be converted to a `Cint`.
