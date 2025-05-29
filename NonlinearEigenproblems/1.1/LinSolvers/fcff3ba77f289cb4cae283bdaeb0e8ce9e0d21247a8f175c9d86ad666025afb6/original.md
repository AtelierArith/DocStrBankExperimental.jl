```
create_linsolver(creator::LinSovlerCreator,nep,λ)
```

Creates a `LinSolver` instance for the `nep` corresponding which is evaluated in `λ`. The type of the output is decided by dispatch and the type of the `LinSolverCreator`.

See also: `LinSolver`, `FactorizeLinSolverCreator`, `BackslashLinSolverCreator`, `DefaultLinSolverCreator`, `GMRESLinSolverCreator`.
