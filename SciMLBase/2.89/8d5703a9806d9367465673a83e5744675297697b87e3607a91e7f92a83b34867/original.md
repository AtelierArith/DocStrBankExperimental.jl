```
remake(prob::SCCNonlinearProblem; u0 = missing, p = missing, probs = missing,
    parameters_alias = prob.parameters_alias, sys = missing, explicitfuns! = missing)
```

Remake the given `SCCNonlinearProblem`. `u0` is the state vector for the entire problem, which will be chunked appropriately and used to `remake` the individual subproblems. `p` is the parameter object for `prob`. If `parameters_alias`, the same parameter object will be used to `remake` the individual subproblems. Otherwise if `p !== missing`, this function will error and require that `probs` be specified. `probs` is the collection of subproblems. Even if `probs` is explicitly specified, the value of `u0` provided to `remake` will be used to override the values in `probs`. `sys` is the index provider for the full system.
