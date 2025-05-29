```
init_mom!(m::WSVarLmmModel, solver; init = init_ls!(m), parallel = false)
```

Initialize `τ` and `Lγ` of a `VarLmmModel` object by method of moment (MoM)  using residulas in `m.obs[i].res`. It involves solving an unweighted NLS problem.

# Position arguments

  * `m`: A `WSVarLmmModel` object.
  * `solver`: NLP solver. Default is `IpoptSolver(print_level=0, mehrotra_algorithm="yes",    warm_start_init_point="yes", max_iter=100)`.

# Keyword arguments

  * `init`: Initlizer for the NLS problem. Default is `init_ls!(m)`. If `init=m`,

then it uses the values provided in `m.τ` and `m.Lγ` as starting point.  

  * `parallel::Bool`: Multi-threading. Default is `false`.
