```
lgl_sat(solver::LglPtr)::Cint
```

Call the main SAT routine. The return values are as above, e.g. `Lingeling.UNSATISFIABLE`, `Lingeling.SATISFIABLE`, or `Lingeling.UNKNOWN`.

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.

# Returns

  * `val::Cint`: The result of the SAT routine. (e.g. `Lingeling.UNSATISFIABLE`,

`Lingeling.SATISFIABLE`, or `Lingeling.UNKNOWN`)
