```
RepeatingAffineFEStateMap(
  nblocks::Int,a::Function,l::Vector{<:Function},
  U0,V0,V_φ,U_reg,φh,dΩ...;
  assem_U = SparseMatrixAssembler(U0,V0),
  assem_adjoint = SparseMatrixAssembler(V0,U0),
  assem_deriv = SparseMatrixAssembler(U_reg,U_reg),
  ls::LinearSolver = LUSolver(),
  adjoint_ls::LinearSolver = LUSolver()
)
```

Create an instance of `RepeatingAffineFEStateMap` given the number of blocks `nblocks`, a bilinear form `a`, a vector of linear form `l` as `Function` types, the trial and test spaces `U` and `V`, the FE space `V_φ` for `φh`, the FE space `U_reg` for derivatives, and the measures as additional arguments.

Optional arguments enable specification of assemblers and linear solvers.

# Note

  * The resulting `FEFunction` will be a `MultiFieldFEFunction` (or GridapDistributed equivalent) where each field corresponds to an entry in the vector of linear forms
