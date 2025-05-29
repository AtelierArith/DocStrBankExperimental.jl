```
output = knitro(nlp; kwargs...)
```

Solves the `NLPModel` problem `nlp` using KNITRO.

For advanced usage, first define a `KnitroSolver` to preallocate the memory used in the algorithm, and then call `solve!`:

```
solver = KnitroSolver(nlp)
solve!(solver, nlp; kwargs...)
solve!(solver, nlp, stats; kwargs...)
```

# Optional keyword arguments

  * `x0`: a vector of size `nlp.meta.nvar` to specify an initial primal guess
  * `y0`: a vector of size `nlp.meta.ncon` to specify an initial dual guess for the general constraints
  * `z0`: a vector of size `nlp.meta.nvar` to specify initial multipliers for the bound constraints
  * `callback`: a user-defined `Function` called by KNITRO at each iteration.

For more information on callbacks, see https://www.artelys.com/docs/knitro/2*userGuide/callbacks.html and the docstring of `KNITRO.KN*set*newpt*callback`.

All other keyword arguments will be passed to KNITRO as an option. See https://www.artelys.com/docs/knitro/3_referenceManual/userOptions.html for the list of options accepted.
