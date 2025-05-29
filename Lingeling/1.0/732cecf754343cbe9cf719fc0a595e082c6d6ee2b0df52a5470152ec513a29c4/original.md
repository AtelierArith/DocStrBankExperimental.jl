```
lgl_hasopt(solver::LglPtr, opt::String)::Cint
```

Check whether an option exists.

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.
  * `opt::String`: The option name.

# Returns

  * `val::Cint`: Whether the option exists. `1` if it exists, `0` otherwise.
