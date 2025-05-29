```
lgl_frozen(solver::LglPtr, lit::Integer)::Cint
```

Check whether a literal is frozen.

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.
  * `lit::Integer`: The literal to check.

# Returns

  * `val::Cint`: Whether the literal is frozen. `1` if it is frozen, `0` otherwise.

# Throws

  * `InexactError`: If the literal can not be converted to a `Cint`.
