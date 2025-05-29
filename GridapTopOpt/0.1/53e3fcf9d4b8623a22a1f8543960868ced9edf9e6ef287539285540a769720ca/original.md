```
NonlinearFEStateMap(
  res::Function,U,V,V_φ,U_reg,φh,dΩ...;
  assem_U = SparseMatrixAssembler(U,V),
  assem_adjoint = SparseMatrixAssembler(V,U),
  assem_deriv = SparseMatrixAssembler(U_reg,U_reg),
  nls::NonlinearSolver = NewtonSolver(LUSolver();maxiter=50,rtol=1.e-8,verbose=true),
  adjoint_ls::LinearSolver = LUSolver()
)
```

Create an instance of `NonlinearFEStateMap` given the residual `res` as a `Function` type, trial and test spaces `U` and `V`, the FE space `V_φ` for `φh`, the FE space `U_reg` for derivatives, and the measures as additional arguments.

Optional arguments enable specification of assemblers, nonlinear solver, and adjoint (linear) solver.
