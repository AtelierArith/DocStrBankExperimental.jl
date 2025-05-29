```
lgl_melt(solver::LglPtr, lit::Integer)
```

Melt a literal meaning that it may be eliminated during `lgl_sat`.

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.
  * `lit::Integer`: The literal to melt.

# Throws

  * `InexactError`: If the literal can not be converted to a `Cint`.
