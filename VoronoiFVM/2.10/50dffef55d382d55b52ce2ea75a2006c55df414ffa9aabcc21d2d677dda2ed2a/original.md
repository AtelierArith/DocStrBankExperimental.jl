```
evaluate_residual_and_jacobian(system,u;
                               t=0.0, tstep=Inf, embed=0.0, init_dirichlet=false)
```

Evaluate residual and jacobian at solution value u. Returns a solution vector containing a copy of  residual, and an ExendableSparseMatrix containing a copy of the linearization at u. The flag `init_dirichlet` controls whether u should be adjusted to satisfy the Dirichlet boundary conditions specified by the system.
