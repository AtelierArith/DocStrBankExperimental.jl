```
residual_snapshots(solver::RBSolver,op::ParamOperator,s::AbstractSnapshots;nparams) -> Contribution
residual_snapshots(solver::RBSolver,op::ODEParamOperator,s::AbstractSnapshots;nparams) -> Contribution
```

Returns a residual `Contribution` relative to the FE operator `op`. The quantity `s` denotes the solution snapshots in which we evaluate the residual. Note that we can select a smaller number of parameters `nparams` compared to the number of parameters used to compute `s`
