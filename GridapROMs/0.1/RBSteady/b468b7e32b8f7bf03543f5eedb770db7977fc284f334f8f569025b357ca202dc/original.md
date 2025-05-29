```
jacobian_snapshots(solver::RBSolver,op::ParamOperator,s::AbstractSnapshots;nparams) -> Contribution
jacobian_snapshots(solver::RBSolver,op::ODEParamOperator,s::AbstractSnapshots;nparams) -> Tuple{Vararg{Contribution}}
```

Returns a Jacobian `Contribution` relative to the FE operator `op`. The quantity `s` denotes the solution snapshots in which we evaluate the jacobian. Note that we can select a smaller number of parameters `nparams` compared to the number of parameters used to compute `s`. In transient settings, the output is a tuple whose `n`th element is the Jacobian relative to the `n`th temporal derivative
