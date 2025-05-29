```
evaluate_residual_and_jacobian(system,u;
                               t=0.0, tstep=Inf,embed=0.0)
```

Evaluate residual and jacobian at solution value u. Returns a solution vector containing the residual, and an ExendableSparseMatrix containing the linearization at u.
