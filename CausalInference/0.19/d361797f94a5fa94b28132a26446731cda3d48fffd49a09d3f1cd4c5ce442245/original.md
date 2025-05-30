```
estimate_equations(t, est_g::DiGraph)::SCM
```

Estimate linear equations from the given table `t` based on the structure of the directed graph `est_g`.

# Arguments

  * `t`: A table containing the data for estimation (supports any Tables.jl-compatible format).
  * `est_g::DiGraph`: A directed graph representing the structure of the SCM.

# Returns

  * `SCM`: A struct containing the estimated variables, their corresponding coefficients, residuals, the DAG, and the causal effects matrix.
