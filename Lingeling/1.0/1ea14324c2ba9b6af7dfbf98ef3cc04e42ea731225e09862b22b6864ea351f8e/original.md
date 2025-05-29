```
lgl_reusable(solver::LglPtr, lit::Integer)::Cint
```

Check whether a literal is reusable. A literal may not have been frozen during the last call to `lgl_sat` but could still be reusable (and thus be made usable again using `lgl_reuse`).

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.
  * `lit::Integer`: The literal to check.

# Returns

  * `val::Cint`: Whether the literal is reusable. `1` if it is reusable, `0` otherwise.

# Throws

  * `InexactError`: If the literal can not be converted to a `Cint`.
