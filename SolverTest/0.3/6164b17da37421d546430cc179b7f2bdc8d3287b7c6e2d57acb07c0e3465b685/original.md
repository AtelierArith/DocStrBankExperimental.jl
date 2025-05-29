```
kkt_checker(nlp, sol; kwargs...)
```

Given an NLPModels `nlp` and a vector `sol`, it returns the KKT residual of an optimization problem as a tuple (primal, dual). In particular, it uses `ripqp` to solve the following quadratic optimization problem with linear constraints

```
min_{d} ∇f(sol)ᵀd +  ½∥d∥²
        lvar ≤ sol + d ≤ uvar
        lcon ≤ c(sol) + ∇c(sol)d ≤ ucon
```

The solution of this problem is the gradient of the Lagrangian of the `nlp` at `sol` thanks to the ½ ‖d‖² term in the objective.

Keyword arguments are passed to `RipQP`.
