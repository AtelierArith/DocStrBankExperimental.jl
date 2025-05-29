```
lgl_setopt(solver::LglPtr, opt::String, val::Integer)
```

Set an option value.

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.
  * `opt::String`: The option name.
  * `val::Integer`: The new option value.

# Throws

  * `InexactError`: If the option value can not be converted to a `Cint`.
