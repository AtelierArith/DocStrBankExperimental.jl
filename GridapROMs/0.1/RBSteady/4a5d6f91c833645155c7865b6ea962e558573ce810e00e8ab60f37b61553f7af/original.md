```
solution_snapshots(solver::NonlinearSolver,feop::ParamOperator,r::Realization) -> SteadySnapshots
solution_snapshots(solver::ODESolver,feop::TransientParamOperator,r::TransientRealization,u0) -> TransientSnapshots
```

The problem encoded in the FE operator `feop` is solved several times, and the solution snapshots are returned along with the information related to the computational cost of the FE method. In transient settings, an initial condition `u0` should be provided.
