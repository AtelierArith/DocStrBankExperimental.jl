```
lgl_add(solver::LglPtr, lit::Integer)
```

Add a literal of the next clause.  A `0` literal terminates the clause.

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.
  * `lit::Cint`: The literal to add. A `0` literal terminates the clause. Negative literals are negated (i.e., `-2` means "NOT 2")

# Throws

  * `InexactError`: If the literal can not be converted to a `Cint`.
