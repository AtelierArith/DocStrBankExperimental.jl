```
lgl_usable(solver::LglPtr, lit::Integer)::Cint
```

Check whether a literal is usable. A literal becomes unusable if it was not frozen during the last call to `lgl_sat`. Being unusable means that the literal is not allowed to be used in the next call to `lgl_add`.

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.
  * `lit::Integer`: The literal to check.

# Returns

  * `val::Cint`: Whether the literal is usable. `1` if it is usable, `0` otherwise.

# Throws

  * `InexactError`: If the literal can not be converted to a `Cint`.
