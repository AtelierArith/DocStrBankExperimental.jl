```
lgl_reuse(solver::LglPtr, lit::Integer)
```

Make a literal usable again. If a literal was not frozen during the last call to `lgl_sat` but is reusable, it can be made usable again using this function.

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.
  * `lit::Integer`: The literal to make reusable again.

# Throws

  * `InexactError`: If the literal can not be converted to a `Cint`.
