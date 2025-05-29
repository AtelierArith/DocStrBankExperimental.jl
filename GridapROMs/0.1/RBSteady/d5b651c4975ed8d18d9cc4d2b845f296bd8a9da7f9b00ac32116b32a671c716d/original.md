```
reduced_spaces(solver::RBSolver,feop::ParamOperator,s::AbstractSnapshots
  ) -> (RBSpace, RBSpace)
```

Computes the subspace of the test, trial `FESpace`s contained in the FE operator `feop` by compressing the snapshots `s`
