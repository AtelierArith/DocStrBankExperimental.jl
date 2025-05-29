```
CPRPreconditioner(p = default_psolve(), s = ILUZeroPreconditioner(); strategy = :quasi_impes, weight_scaling = :unit, update_frequency = 1, update_interval = :iteration, partial_update = true)
```

Construct a constrained pressure residual (CPR) preconditioner.

By default, this is a AMG-BILU(0) version (algebraic multigrid for pressure, block-ILU(0) for the global system).
