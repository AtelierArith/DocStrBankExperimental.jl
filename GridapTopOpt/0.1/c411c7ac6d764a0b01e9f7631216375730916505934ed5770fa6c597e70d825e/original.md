```
AffineFEStateMap(
  a::Function,l::Function,
  U,V,V_φ,U_reg,φh,dΩ...;
  assem_U = SparseMatrixAssembler(U,V),
  assem_adjoint = SparseMatrixAssembler(V,U),
  assem_deriv = SparseMatrixAssembler(U_reg,U_reg),
  ls::LinearSolver = LUSolver(),
  adjoint_ls::LinearSolver = LUSolver()
)
```

Create an instance of `AffineFEStateMap` given the bilinear form `a` and linear form `l` as `Function` types, trial and test spaces `U` and `V`, the FE space `V_φ` for `φh`, the FE space `U_reg` for derivatives, and the measures as additional arguments.

Optional arguments enable specification of assemblers and linear solvers.
